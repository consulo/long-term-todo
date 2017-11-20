Current classloader rule

distribution:
 /bin
 /lib
 /plugins/
 /plugins/platform-independent-plugin/
 /plugins/platform-desktop-plugin/

1. Bootclassloader load - consulo-desktop-boot & jna & jna-platform & util & util-rt (from /lib directory)
2. In boot space creating **platform** classloader from /lib directory (eat all jars) - it means we duplicate loading boot jars in memory
3. **platform** classloader init applications - and load plugins from directories
