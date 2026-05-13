## Reflection

**a. How much data your publisher program will send to the message broker in one run?**

Program publisher mengirimkan 5 event/message dalam satu kali program dijalankan. Hal ini karena terdapat lima 
pemanggilan fungsi `publish_event()` yang masing-masing mengirim data user berbeda ke message broker.

**b. The url `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?**

URL "amqp://guest:guest@localhost:5672" merupakan alamat koneksi yang digunakan publisher untuk terhubung ke RabbitMQ. 
URL tersebut berisi protokol AMQP, username, password, host, dan port yang digunakan untuk komunikasi dengan message 
broker.

<br>

### Running RabbitMQ
![RabbitMQ Home Page](/img/RabbitMQ.png)

### Sending and Processing Event

![Sending and Processing Event](/img/Sending-Processing-Event.png)

Pada percobaan ini, publisher dan subscriber berhasil terhubung dengan RabbitMQ sebagai message broker. Ketika 
program publisher dijalankan menggunakan `cargo run`, publisher mengirimkan 5 event ke RabbitMQ dengan data user 
yang berbeda.

Subscriber yang sedang berjalan kemudian menerima dan memproses setiap event tersebut. Hal ini terlihat pada 
console subscriber yang menampilkan message seperti `UserCreatedEventMessage` beserta `user_id` dan `user_name`.

Pada console RabbitMQ juga terlihat adanya koneksi AMQP yang menunjukkan bahwa publisher dan subscriber 
berhasil terhubung ke message broker menggunakan protokol AMQP. Setiap kali publisher dijalankan kembali, 
RabbitMQ menerima event baru dan meneruskannya ke subscriber untuk diproses.

Percobaan ini menunjukkan bagaimana event-driven architecture memungkinkan publisher dan subscriber 
berkomunikasi secara asynchronous melalui message broker tanpa harus saling terhubung secara langsung.


### Monitoring Chart

![Monitoring Chart](/img/Monitoring-Chart.png)

Saat publisher dijalankan berkali-kali, terlihat adanya spike pada chart RabbitMQ. Hal ini terjadi karena publisher 
mengirim banyak message ke message broker dalam waktu singkat. RabbitMQ kemudian menerima dan menyimpan message 
tersebut di queue sebelum diproses oleh subscriber. Semakin sering publisher dijalankan, semakin tinggi spike yang 
muncul pada chart karena jumlah message yang masuk meningkat.