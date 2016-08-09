# Parsing an XML Feed

## Overview

This guide covers how to parse an XML content feed using a task node in SceneGraph. Parsing an XML feed is one of the most common ways to retrieve content for Roku channels. This guide will be using an example feed supplied by Roku.

**Steps:**

1. [Create Task node](#1-create-task-node)
2. [Retrieve XML content feed](#2-retrieve-xml-content-feed)
3. [Parse XML content feed](#p3-arse-xml-content-feed)
4. [Setup Task thread](#4-setup-task-thread)
5. [Addendum: Customizing grid size](#5-addendum-customizing-grid-size)

## 1. Create Task Node

First create a new XML file in the `components` folder called `FeedParser`. This component extends from the `Task` node class. Also create an interface field called `content` to store each item in the parsed XML feed.

```xml
<component name="FeedParser" extends="Task">

    <interface>
        <field id="content" type="node" />
    </interface>
```

## 2. Retrieve XML content feed

Next, make a curl request to the feed and store its response.

```brightscript
Function GetApiArray() 'This function makes a curl request and parses through all its content
    url = CreateObject("roUrlTransfer") ' Curl command object
    url.SetUrl("http://api.delvenetworks.com/rest/organizations/59021fabe3b645968e382ac726cd6c7b/channels/1cfd09ab38e54f48be8498e0249f5c83/media.rss")
    rsp = url.GetToString() 'Turns response into a string
```

## 3. Parse XML content feed

Then we have to parse the response string using the `ParseXML` method. `ParseXML` is a function that will try to parse the response string on the `XMLElement` or return `invalid` if it fails.

```brightscript
Function ParseXML(str As String) As dynamic 'Takes in response from curl request
    if str = invalid return invalid  'if the response is invalid it returns invalid
    xml = CreateObject("roXMLElement") '
    if not xml.Parse(str) return invalid 'If the response cannot be parsed, it returns invalid
    return xml 'returns parsed XML if not invalid
End Function
```

### Manually parse feed if ParseXML() is invalid

In a fallback case when it returns `invalid`, the response will have to be parsed manually.

```brightscript
responseXML = ParseXML(rsp) 'Roku includes it's own XML parsing method
If responseXML<>invalid then  'Fall back in case Roku's built in XML Parse method fails
    responseXML = responseXML.GetChildElements() 'Access content inside Feed
    responseArray = responseXML.GetChildElements()
End If

result = [] 'Store all results inside an array. Each element represents a row inside our RowList stored as an Associative Array (line 63)

for each xmlItem in responseArray 'For loop to grab content inside each item in the XML feed
    if xmlItem.getName() = "item" 'Each individual channel content is stored inside the XML header named <item>
        itemAA = xmlItem.GetChildElements() 'Get the child elements of item
        if itemAA <> invalid 'Fall back in case invalid is returned
            item = {} 'Creates an Associative Array for each row
            for each xmlItem in itemAA 'Goes through all content of itemAA
                item[xmlItem.getName()] = xmlItem.getText()
                if xmlItem.getName() = "media:content" 'Checks to find <media:content> header
                    item.stream = {url : xmlItem.url} 'Assigns all content inside <media:content> to the item AA
                    item.url = xmlItem.getAttributes().url
                    item.streamFormat = "mp4"

                    mediaContent = xmlItem.GetChildElements()
                    for each mediaContentItem in mediaContent 'Looks through MediaContent to find poster images for each piece of content
                        if mediaContentItem.getName() = "media:thumbnail"
                            item.HDPosterUrl = mediaContentItem.getattributes().url 'Assigns images to item AA
                            item.hdBackgroundImageUrl = mediaContentItem.getattributes().url
                        end if
                    end for
                end if
            end for
            result.push(item) 'Pushes each AA into the Array
        end if
    end if
end for
return result ' Returns the array
End Function
```

_Note that this may change based on the format of the response._

## 4. Setup Task thread

Next, we setup the task node to call these functions when initialized. Because the `init()` method spawns on the render thread and we want the task node to run on a separate task thread, we setup the `init()` function to spawn a separate function on the task thread.

```brightscript
Sub Init()
    m.top.functionName = "loadContent"
End Sub

Sub loadContent()
    oneRow = GetApiArray()
    list = [
        'first row in the grid with 3 items across
        {
            Title:"Row One"
            ContentList : SelectTo(oneRow, 3)
        }
        'second row in the grid with 5 items across
        {
            Title:"Row Two"
            ContentList : SelectTo(oneRow, 5)
        }
        'third row in the grid with 15 items across
        {
            Title:"Row Three"
            ContentList : SelectTo(oneRow, 15)
        }
        'fourth row in the grid with 5 items across
        {
            Title:"Row Four"
            ContentList : SelectTo(oneRow, 5)
        }
    ]
    m.top.content = ParseXMLContent(list)
End Sub
```

The function `loadContent()` assigns the variable `oneRow` as an array that contains all the content from the feed. `list` is then assigned as an Array of Associative Array elements containing the title of each row and the content to be loaded.

`list` is passed into a separate function named `ParseXMLContent` that takes all of the content and assigns them to content nodes that can be passed into a `RowList` component. The formatted content node is then passed into the content field of the task node so it can accessed from outside the scope of the task thread.

```brightscript
Function ParseXMLContent(list As Object) 'Formats content into content nodes so they can be passed into the RowList
    RowItems = createObject("RoSGNode","ContentNode")
    'Content node format for RowList: ContentNode(RowList content) --<Children>-> ContentNodes for each row --<Children>-> ContentNodes for each item in the row)
    for each rowAA in list
        row = createObject("RoSGNode","ContentNode")
        row.Title = rowAA.Title

        for each itemAA in rowAA.ContentList
            item = createObject("RoSGNode","ContentNode")
            item.SetFields(itemAA)
            row.appendChild(item)
        end for
        RowItems.appendChild(row)
    end for
    return RowItems
End Function
```

## 5. Addendum: Customizing grid size

Optionally, the following method can be used to adjust the number of items for each row in the grid. This simple function allows for customizable non-rectangular grids.

_Note: This method is used in the example above and called for each row in the grid in `loadContent()`._

```brightscript
function SelectTo(array as Object, num = 25 as Integer) as Object 'This method copies an array up to the defined number "num" (default 25)
    result = []
    for each item in array
        result.push(item)
        if result.Count() >= num
            exit for
        end if
    end for
    return result
end Function
```
