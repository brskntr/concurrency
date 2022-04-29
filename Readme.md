## Java Concurrency


### Volatile

volatile for flags

Thread 1 and Thread 2 uses same flag. Let's say;
public boolean visible = true;

Thread-1 changes as visible = false

Thread-2 : 
while(visible){
  // processing 
}

We want to do that if Thread-1 changes visible as false Thread-2 will break the while loop but for now not able to do this.

We have to put volatile
public volatile boolean visible = true;

finally Thread-2 can read the updated value for visible then can exit the loop.

### Syncronized

syncronized for counters

Thread 1 and Thread 2 incerement the value;
public int value = 1;

we have to put syncronized around increment logic because Thread 1 and Thread 2 read the value as 1 before increased.
syncronized(value){
  value++;
}

Other solution is 

### AtomicInteger

AtomicInteger value = AtomicInteger(1);
no need to syncronized and just value.increment(); 

The other methods available 
// decrement
// decrementAndGet
// incrementAndGet
// compareAndSet(compareValue,newValue)

