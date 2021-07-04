# Create and use a new thread

Simple code example:

```cpp
void DoSomething() {
  std::cout << "Wulala Ohleilei" << std::endl;
}

int main() {
  // We have a "main" thread now and we're now in this "main" thread.
  
  // Define a new thread.
  // We can pass in a function pointer (or nothing) into this new thread.
  // The "DoSomething" shown below does not have a "()" after it since it's a function pointer!
  std::thread my_new_thread(DoSomething);

  // This means: Pause (or namely "lock") the main thread until the thread "my_new_thread" is done.
  // So whatever is happening in the main thread will be paused, until whatever is to be happen
  // inside "my_new_thread" are finished.
  my_new_thread.join();
}
```
