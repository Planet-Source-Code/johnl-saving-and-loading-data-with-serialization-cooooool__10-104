<div align="center">

## Saving and Loading Data with Serialization \-\- cooooool


</div>

### Description

Save entire classes or structs at a time to an xml file, and then read them back.
 
### More Info
 
File to save as?

An Object.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[JohnL](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/johnl.md)
**Level**          |Intermediate
**User Rating**    |4.4 (22 globes from 5 users)
**Compatibility**  |VB\.NET
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__10-2.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/johnl-saving-and-loading-data-with-serialization-cooooool__10-104/archive/master.zip)





### Source Code

```
Imports System.Xml.Serialization
Public Class Settings
  'or Struct
  'this is our class that holds all our settings.
  Public RandomSetting As Integer
  Public RandomString As String
  'etc.
End Class
  Public Sub SaveSettings(ByRef mypath As String, ByRef mySettings As Settings)
    Dim XmlS As New XmlSerializer(GetType(Settings))
    Dim fStream As New IO.FileStream(mypath, IO.FileMode.Create)
    XmlS.Serialize(fStream, mySettings)
    fStream.Close()
    fStream = Nothing
    XmlS = Nothing
  End Sub
  Public Function LoadSettings(ByRef mypath As String) As Settings
   Dim XmlS As New XmlSerializer(GetType(Settings))
    Dim fStream As New IO.FileStream(mypath, IO.FileMode.Open)
    Return XmlS.Deserialize(fStream)
  End Function
USAGE
 Dim R as New Settings() 'to save
 Dim S as New Settings() 'to load
 R.RandomSetting = 12
 R.RandomString = "~)!~~"
 SaveSettings("C:\mySettings.xml",R)
 S = LoadSettings("C:\mySettings.xml")
 Msgbox(S.RandomSetting & " " & S.RandomString)
```

