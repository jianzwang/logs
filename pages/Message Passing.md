public:: true

- > “Do not communicate by sharingmemory; instead, share memory by communicating.”
- ((623757c0-c06d-4dcb-9b18-1e92f4d256bf))
- A channel in programming has two halves: a transmitter and a receiver.
	- One part of your code calls methods on the transmitter with the data you want to send, and another part checks the receiving end for arriving messages. A channel is said to be closed if either the transmitter or receiver half is dropped.
- mpsc was an acronym for multiple producer, single consumer.
- The abbreviations **tx** and **rx** are traditionally used in many fields for transmitter and receiver respectively, so we name our variables as such to indicate each end.
- **send**
	- The **send** method returns a Result<T, E> type
	- The **send** function takes ownership of its parameter, and when the value is moved #ownership
- **recv** and **try_recv**
	- **recv** will block the thread's execution and wait until a value is sent down the channel. Once a value is sent, **recv** will return it in a Result<T, E>. When the sending end of the channel closes, **recv** will return an error to signal that no more values will be coming.
	- **try_recv** method doesn’t block, but will instead return a Result<T, E> immediately: an Ok value holding a message if one is available and an Err value if there aren’t any messages this time. Using **try_recv** is useful if this thread has other work to do while waiting for messages: we could write a loop that calls **try_recv** every so often, handles a message if one is available, and otherwise does other work for a little while until checking again.
- Creating Multiple Producers by Cloning the Transmitter
- ```rust
  use std::sync::mpsc;
  use std::thread;
  use std::time::Duration;
  fn main() {
    let (tx, rx) = mpsc::channel();
    thread::spawn(move || 
      {
        let vals = vec![
          String::from("hi"),
          String::from("from"),
          String::from("the"),
          String::from("thread"),
          ];
        for val in vals {
          tx.send(val).unwrap();
          thread::sleep(Duration::from_secs(1));
        }  
    	}
    );
    for received in rx {
      println!("Got: {}", received); 
    }
  }
  ```
- channels in any programming language are similar to single ownership, because once you transfer a value down a channel, you should no longer use that value.