# Soal test maggang Quality Assurance engineer

Berikut adalah soal/pertanyaan yang perlu dijawab oleh peserta

## knowledge base

1. Apa yang anda ketahui tentang Rest API?

    REST (Representational State Transfer) API adalah salah satu tipe API, yaitu set fungsi yang membantu developer untuk melakukan request dan mendapatkan response. Interaksi yang terjadi menggunakan HTTP protocol pada REST API. Request data dari server menggunakan HTTP Method (GET, POST, PUT, dan DELETE) sedangkan response return data dari server. 
    GET: retrieve data dari server
    POST: add data pada server
    PUT: replace data yang sudah ada di server
    DELETE: delete data dari server
    Selain data, response juga return HTTP status code yang menyatakan benar atau tidaknya suatu request dan response atau menyatakan kesalahan yang terjadi pada server. Beberapa contoh status code:
    200: OK -> request success dan complete
    201: Created -> request created
    400: Bad Request -> request invalid
    401: Unauthorized -> there is no authentication token atau token expired
    500: Internal Server Error -> error pada server
    API juga dapat meningkatkan security dengan menggunakan API keys, biasanya digunakan ketika login sebagai authentication credentials.

3. Apa yang anda ketahui tentang Server side and Client side processing?
Server Side Processing: proses yang dijalankan di server web, membutuhkan interaksi dengan server,seperti Query dan update database server, security, kalkulasi kompleks, dan validasi.

    Client Side Processing: proses dijalankan di perangkat user, berkaitan dengan yang dilihat oleh user seperti load user interface element, CSS.

3. Apa yang anda ketahui tentang Monolith dan Microservices, berikan contohnya?
    Monolith yaitu simple arsitektur aplikasi sebagai 1 unit, biasanya digunakan pada aplikasi yang tergolong kecil dan tidak kompleks. Contohnya, small e-commerce app dengan fitur list products, filter per categories atau brand, put product to the shopping cart, apply coupon, checkout and create order, list history of orders. Dimana aplikasi hanya akan diakses oleh beberapa user saat bersamaan. Monolithic architecure terdiri dari Client, Server, dan Database.

    Microservices adalah kompleks arsitektur aplikasi yang memiliki banyak service dan saling berkomunikasi. Setiap service memiliki fungsi masing-masing. Contohnya, aplikasi e-commerce pada contoh monolith sebelumnya, namun, memiliki jutaan request yang bersammaan dan meningkat hari demi har. Sehingga akan terdapat beberapa service, yaitu product, cart, order yang memiliki databasenya masing-masing dan setiap service berkomunikasi satu sama lain lewat API.

4. Apa yang anda ketahui tentang Automation testing serta sebutkan contohnya?
    Automation testing adalah proses penggunaan tool untuk mengotomatiskan eksekusi test case. Cara kerja automation testing yaitu menggunakan script untuk mensimulasikan action dari user ketika menggunakan aplikasi untuk cek fungsi maupun performance sebuah aplikasi.

    Keuntungan menggunakan automation testing adalah mempercepat pekerjaan yang berulang-ulang dam mempercepat proses eksekusi test case sehingga dapat menghemat waktu. Namun, tidak semua manual test dapat di otomatiskan, contohnya Google CAPTCHA. Automation testing dapat digunakan unruk regression testing, functional testing, compatibility testing, API testing dan performance testing.

    Regression testing sangat disarankan untuk dilakukan secara otomatis dikarenakan regression testing dilakukan ketika terjadi perubahan pada aplikasi (dapat berupa perbaikan atau penambahan fitur baru) dan aplikasi harus dilakukan test pada fitur-fitur yang terkait sehingga test case untuk regression testing sangat besar. Oleh karena itu, dengan memanfaatkan automation testing dapat mempercepat dan mempermudah proses eksekusi regression testing.

    Compatibility testing yaitu untuk memastikan bahwa aplikasi dapat sesuai ekspetasi berkaitan dengan berbagai kondisi perangkat lunak seperti device, browser, maupun OS. Banyak automation testing tools yang menyediakan pilihan kondisi perangkat lunak yang akan dilakukan test. Sehingga penggunaan automation testing untuk compatibility test sangat mempermudah.

    Performance testing harus menggunakan automation testing dikarenakan akan sangat sulit apabila dilakukan secara manual. Contohnya cek bagaimana aplikasi web menghandle ketika 100 user login pada saat yang bersamaan atau dalam kondisi bad connection dan lainnya.

    Pada dasarnya automation testing bertujuan untuk meningkatkan efisiensi testing, mengurangi cost, dan mempercepat eksekusi test case.

5. Dengan menggunakan tools automation testing tersebut, biasanya menggunakan bahasa/tools apa?
    Banyak sekali automation testing tools, diantaranya yang banyak digunakan adalah 
- Katalon
- Robot Framework menggunakan python
- Selenium
- Appium
- Cypress
- Postman dan JMeter untuk API test
- JMeter dan k6 untuk performance test

## Use cases

Suppose there was a transaction that had been done in tokopedia.com , the transaction
id should be available on the screen alongside with the address of shipment, date of
order, seller’s name, and delivery service (JNE/POS/REX/others). 
The transaction id (TRX_ID) should also be available on the database which again supposedly there was a simple table containing all the transaction data.

![success notif](imgs/trx-notif.png)

![tabel transaksi](imgs/table-trx.png)

Apparently, the order `01023A9AC` seems to have different Delivery Service on the UI and the
database record. How do you, as automation test developers develop such test scenario so that
this kind of error does not occur?

Test Scenario:
 1. User melakukan transaksi berhasil dengan berbagai delivery service (JNE/POS/REX/others) dengan expected result:
    - Transaksi berhasil
        -- Transaction Successful alert is shown
        -- There is Transaction ID

    - Data transaksi yang ditampilkan, sesuai dengan yang user input.
        -- The name of Seller is correct
        -- Delivery Service is correct
        -- Date order is correct
        -- Address Shipment is correct

Melakukan API testing dan cek pada database, apakah response data sesuai dengan data pada database
- POST
        -- Create transaction with JNE
        -- Create transaction with POS
        -- Create transaction with REX
        -- Create transaction with others
- GET
        -- get all list transaction with specific seller
        -- get transaction with specific Transaction ID

Dengan melakukan testing tersebut, deffct tersebut akan terdeteksi. Apabila terdapat defect, akan diketahui darimana asal defect itu terjadi, apakah dari sisi tampilan kepada user, API atau database.
