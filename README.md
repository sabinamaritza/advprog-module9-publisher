## Reflection

**a. How much data your publisher program will send to the message broker in one run?**

Program publisher mengirimkan 5 event/message dalam satu kali program dijalankan. Hal ini karena terdapat lima 
pemanggilan fungsi `publish_event()` yang masing-masing mengirim data user berbeda ke message broker.

**b. The url `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?**

URL "amqp://guest:guest@localhost:5672" merupakan alamat koneksi yang digunakan publisher untuk terhubung ke RabbitMQ. 
URL tersebut berisi protokol AMQP, username, password, host, dan port yang digunakan untuk komunikasi dengan message 
broker.