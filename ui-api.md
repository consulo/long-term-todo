Consulo provide UI API - implementation will be work at Desktop & Web Browsers. Consulo UI API is not compatible to Swing or Vaadin

Desktop implementation based on **Swing**, and Web on **GWT** (with **Vaadin** as transport + ui system)

For default - any plugins don't known about **Swing** or **GWT**

Classes:

 * ```consulo.ui.UIAccess``` - class provide access to UI Thread, and allow get current thread status
   * ```#isUIThread()``` - will return true if we inside UI Thread
   * ```#give(Runnable)``` - run task inside UI Thread
   * ```#get()``` - will return UIAccess instance if call inside UI thread, otherwise throw exception



# Different Swing vs Consulo API
 * Showing dialogs **not block current thread**
