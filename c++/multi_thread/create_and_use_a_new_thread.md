# Create and use a new thread

Simple code example:

```cpp
static bool done = false;

void DoSomething() {
  while (!done) {
    std::cout << "Not done yet!" << std::endl;
    std::this_thread::sleep_for(1s);
  }
}

int main() {
  // We have a "main" thread now and we're now in this "main" thread.
  
  // Define a new thread, and this thread will begin to run immediately!
  // We can pass in a function pointer or nothing into this new thread to make it run something
  // or run nothing.
  // The "DoSomething" shown below does not have a "()" after it since it's a function pointer!
  std::thread my_new_thread(DoSomething);
  
  // The following code exist and happen in the main thread.
  // std::cin.get() is essentially a while loop that goes on forever until the user press "Enter"
  // in the key board. So what happens here is:
  // * Before this line, the "branch" thread "my_new_thread" is already running continuously.
  // * std::cin.get() is waiting the user to press Enter, if the user does not press Enter, the
  //   code will never reach the next line of "done = true;".
  // * When the user press Enter, std::cin.get() will get it, and we can go to the next line of
  //   setting "done" to true. And don't forget at this time the "my_new_thread" thread is still
  //   running "under the hood" just like before!
  // * The variable "done" is set to "true", and "my_new_thread" got this change since it has a 
  //   while loop that is continuously checking this var. Then the while loop in that thread is
  //   ended. So "my_new_thread" finished everything that is inside it. Then we go to the 
  //   "my_new_thread.join()" below in the main thread. See more details in the comment below.
  std::cin.get();
  done = true;

  // This means: Pause (or namely "lock") the main thread until the thread "my_new_thread" is done.
  // So whatever is happening in the main thread will be paused, until whatever is to be happen
  // inside "my_new_thread" are finished.
  my_new_thread.join();
  std::cout << "Done!" << std::endl;
}
```
