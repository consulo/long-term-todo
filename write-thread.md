By historical reason - all write actions in IDEA(Consulo) must be wrapped in AWT Thread + write lock.

Why this bad
 * long write actions block interface
 * most operations are synchronous
 * when work on web-server, AWT thread must be replaced per Application (since more than one Application can exists in on JVM instance)

TODO
 * create background thread, with id **Consulo Write Thread**, where all operations will be processed
 * **synchronous write operation in UI thread must be restricted**
 
