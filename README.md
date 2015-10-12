# HVTHhandler
Utility methods that provide advanced functionality when using Runnables on Android.

Sometimes you want to post a runnable and wait until it finishes, or even get a return value. This type of funcionlity and even more advnded features can be provided by Future and Executors. However, it's quite common that you just want to stick with Handlers, HandlerThread for doing things you way. These methods will make your live easier.

### Post runnable and wait
``` java
void yourMethod() {
    // the call will block
    HVTHandler.postAndWait(mHandler, new Runnable() {
                @Override
                public void run() {
                    // do stuff on the other thread
                }
            });
    // do stuff on the calling thread after the runnable has finished
  }
```

### Post runnable and get a return value

``` java
void yourMethod() {
        RunnableResult<Integer> result = HVTHandler.post(mHandler, new RunnableValue<Integer>() {
            @Override
            public void run() {
                //do stuff on the other thread and update the return value
                value = 2;
            }
        });
        // Do other stuff on the calling thread, while the runanble is running
        
        // block until it finishes and get the return value
        int resultValue = result.get();
    }
```
