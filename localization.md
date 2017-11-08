# Want
  * allow to set key -> value mapping
     * [X] java resource bundle
     * [X] xml 
     * [X] yaml
  * easy way for write bundles
     * [X] java resource bundle
     * [ ] xml
        * problem with escaping, and lt-gt and other symbols will be pain
     * [X] yaml
  * optional functional for special conditions
     * [ ] java resource bundle
        * contains inline simple condition syntax (for example check is arg is zero, etc - like create text 'mouse' or 'mouses' depending to argument)
     * [X] xml
     * [X] yaml
  * impl
     * [X] java resource bundle
     * [ ] xml 
     * [ ] yaml
 
 # Java Resource Bundle 
 
 ```properties
 settings.title=Settings
 settings.title.mac=Preferences
 ```
 
 # YAML
 
 ```yaml
 --- 
maybe.action: 
  text: "Maybe ?"
message.with.mnenonic: 
  text: dada&gdsdsgsdgds
settings.title: 
  os: 
    mac: Preferences
  text: Settings
text.with.semicolon: 
  text: "Label:"

 ```
