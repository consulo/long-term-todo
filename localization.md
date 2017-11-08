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
   * generate Java file with keys
     
 # Result
 ### YAML

 
 # YAML
 CommonLocalize.yaml
 
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
text.with.arg: 
  text: "Label: {0}"

 ```
 # Localize API
 LocalizeKey.java
 ```java
 public interface LocalizeKey  {
   LocalizeValue getValue(Object arg);
   
   LocalizeValue getValue(Object arg0, Object arg1);
   
   LocalizeValue getValue(Object arg0, Object arg1, Object arg2);
   
   LocalizeValue getValue(Object arg0, Object arg1, Object arg2, Object arg3);
   
   LocalizeValue getValue(Object arg0, Object arg1, Object arg2, Object arg3, Object arg4);
 }
 ```
 
 LocalizeValue.java
 ```java
 public interface LocalizeValue {
   String getValue();
   
   String getValue(Locale locale);
 }
 ```

 # YAML to Java generator
 
 Rules:
  * must be placed at `/src/main/resources/localize` directory
  * unique name per application (like use plugin prefixes, JavaLocalize, CSharpLocalize, etc)
  * generated class will be placed in **localize** package with same name as **yaml** file (without extension)
  * Max argument value is 5 (do not use varargs for creating dummy object arrays)
 
 /messages/CommonLocalize.java
```java
public class CommonLocalize {
  private static final Localize ourLocalize = Localize.load(this);
  
  private static final LocalizeKeyAsValue ourMaybeTitleKey = new LocalizeKeyAsValue(ourLocalize, "maybe.title");
  
  public static LocalizeValue maybeTitle() {
     return ourMaybeTitleKey;
  }
  
  private static LocalizeKey ourTextWithArgKey = new LocalizeKey(ourLocalize, "text.with.arg");
  
  public static LocalizeValue textWithArg(Object arg) {
     return ourTextWithArgKey.getValue(arg);
  }
}
```
 
