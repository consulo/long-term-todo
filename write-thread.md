By historical reason - all write actions in IDEA(Consulo) must be wrapped in AWT Thread + write lock.

Why this bad
 * long write actions block interface (for example FS event handling)
 * most operations are synchronous (AWT show)
 * when work on web-server, AWT thread must be replaced per Application (since more than one Application can exists in on JVM instance)

Changes:
 * Write actions migrated to OWN thread, UI thread now not provide implicit read access
 * all AWT dialogs now async - that why, all code based on this logic now not work as expected
 * Removing consulo.platform.Platform#hacky method, since opening project now always async
 * Unify base code (desktop<->web), since we migrated to UIAccess usage
