# State: Implemented

### Current loader:

platform distribution:
```
 /bin
 /lib
 /plugins/
 /plugins/platform-independent-plugin/
 /plugins/platform-desktop-plugin/
```

1. Bootclassloader load - consulo-desktop-boot & jna & jna-platform & util & util-rt (from /lib directory)
2. In boot space creating **platform** classloader from /lib directory (eat all jars) - it means we **duplicate** loading boot jars in memory
3. **platform** classloader init applications - and load plugins from directories

4. Plaform classes have hardcoded pluginID **com.intellij** it means, desktop plugins can't throw exception with own pluginID - it will be always platform ID

### New loader

 * extract boot part from main loader - do not duplicate it 
 * desktop & web modules must have own pluginID - not platform
 * StartupManager must be in platform code - not boot 

```
/bin
/modules/
/modules/platform-independent/
/modules/platform-independent/lib/
/modules/platform-desktop/lib
````
