#### Nama : Muh. Kemal Lathif Galih Putra
#### NPM : 2206081225
#### Kelas : ADPRO - A
#### ASDOS : REN
#### Link Deployment: [Eshop-Kemal](https://production-qemul-adpro-eshop.koyeb.app/)

# TUTORIAL - 5
### ScreenShoot JMeter Test Plans Before Profiling
### GUI Version
#### Test Plan 1 (all-student)
![all-student_beforeProfiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fall-student_beforeProfiling.png)

#### Test Plan 2 (all-student-name)
![all-student-name_before_profiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fall-student-name_before_profiling.png)

#### Test Plan 3 (highest-gpa)
![highest_gpa_before_profiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fhighest_gpa_before_profiling.png)

### CLI Version
#### Test Plan 1 (all-student)
![all-student-cli_beforeProfiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fall-student-cli_beforeProfiling.png)

#### Test Plan 2 (all-student-name)
![all-student-name-cli_before_profiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fall-student-name-cli_before_profiling.png)

#### Test Plan 3 (highest-gpa)
![highest_gpa_cli_before_profiling.png](hasil_ss_tutor5%2FBefore_Profiling%2Fhighest_gpa_cli_before_profiling.png)

### ScreenShoot JMeter Test Plans After Profiling (Optimization)
#### Test Plan 1 (all-student)
![all-student_after_profiling.png](hasil_ss_tutor5%2FAfter_Profiling%2Fall-student_after_profiling.png)

#### Test Plan 2 (all-student-name)
![all-student-name_after_profiling.png](hasil_ss_tutor5%2FAfter_Profiling%2Fall-student-name_after_profiling.png)

#### Test Plan 3 (highest-gpa)
![highest-gpa_after_profiling.png](hasil_ss_tutor5%2FAfter_Profiling%2Fhighest-gpa_after_profiling.png)

### Analisis dan Kesimpulan
Dari hasil Jmeter yang didapatkan dapat dilihat untuk masing-masing test_plan:
1. `all-student`
   
    - Pada test plan ini, latency yang menandakan waktu ditempuhnya request dieksekusi dalam code sebelum profiling mencapai 
    560k - 570k-an ms latency. 

    - Setelah dilakukan profiling (optimisasi method getAllStudentWithCourses) dapat dilihat bahwa latency nya menurun hingga
   sekitar 24k-an ms latency.

    Hal ini menunjukkan bahwa dengan dilakukan profiling, waktu eksekusi code dapat dipercepat hingga 20x lipat atau teroptimisasi
    hingga persentase 95% lebih cepat. Berarti kita berhasil melakukan profiling pada method / test plan ini.


2. `all-student-name`

    - Pada test plan ini, latency yang dikeluarkan sebelum profiling sekitar 20k-an ms latency.
    - Setelah dilakukan profiling (optimisasi method joinStudentNames) dapat dilihat bahwa latency nya menurun hingga 300 - 700 an ms latency.
    
    Hal ini menunjukkan bahwa dengan dilakukan profiling, waktu eksekusi code dapat dipercepat hingga 30x lipat atau teroptimisasi hingga
    96.5% lebih cepat. Hal ini berarti kita berhasil melakukan profiling pada method / test plan ini.


3. `highest-gpa`
    
    - Pada test plan ini, latency yang dikeluarkan sebelum profiling sekitar 230-an ms latency.
    - Setelah dilakukan profiling (optimisasi method getStudentWithHighestGPA) dapat dilihat bahwa latency nya menurun hingga 10 - 30 an ms latency.

    Hal ini menunjukkan bahwa dengan dilakukan profiling, waktu eksekusi code dapat dipercepat hingga 8x lipat atau teroptimisasi hingga sekitar 87% lebih cepat daripada sebelum optimasi.
    Ini berarti kita juga telah berhasil melakukan profiling pada method / test plan ini.

## Refleksi
1. Pendekatan pengujian menggunakan JMeter tidak menyangkut cara program/aplikasi beroperasi, sehingga kadang disebut seperti blackbox. 
   JMeter hanya perlu mengirim permintaan ke endpoint yang ditentukan dan menyesuaikan jumlah permintaan sesuai dengan permintaan penguji. Dilain hal, dengan profiling, kita bisa mengetahui bagian program mana saja yang lebih lama berjalan dibandingkan dengan program lain
   sehingga kita bisa melakukan optimasi pada bagian-bagian kode kita yang tercap "besar".


2. Profiling membantu kita dalam mengetahui bagian program mana yang menghambat kinerja aplikasi secara keseluruhan (memory, cpu, time, etc). 
   Dengan demikian, kita hanya perlu mengoptimasi bagian yang tercap tersebut sehingga aplikasi secara keseluruhan akan meningkat kinerjanya dengan lebih baik tanpa perlu memperbaiki terlalu banyak bagian dari keseluruhan code nya.


3. Menurut saya iya, profiler Intelij efektif dalam membantu saya untuk menganalisa method atau kode mana
   yang mengalami kehambatan yang tidak diperlukan. Lebih dalamnya, dengan profiler Intellij, saya dapat 
   mengetahui bagian program yang memakan waktu paling lama, seperti method getAllStudentWithCourses etc. 
   Bahkan, dengan informasi durasi waktu yang diperlukan untuk mengoperasikan pemanggilan-pemanggilan fungsinya, saya dapat mendeteksi baris mana pada method tersebut yang menghambat kinerja methodnya.


4. Menurut saya, membaca output dari alat pengujian performansi dan profiler merupakan tantangan besar. Diperlukan pemahaman yang mendalam untuk mengidentifikasi bagian program yang menjadi bottleneck. 
   Tentu solusinya adalah bisa dengan membiasakan diri dengan teknologi baru ini untuk lebih mudah mendapatkan informasi penting dari hasil outputnya.


5. Dengan bantuan profiler Intellij, kita dapat mengidentifikasi bagian program yang menjadi biang permasalahan, 
durasi eksekusi suatu metode, dan frekuensi pemanggilan metode. Ini memungkinkan kita untuk mengoptimalkan bagian program yang membutuhkan perhatian tanpa mengabaikan prinsip bahwa melakukan optimasi terlalu dini dapat mengurangi keterbacaan kode.


6. Dari hasil "gs-gs" diketahui bahwa untuk menangani situasi di mana hasil dari profilisasi menggunakan IntelliJ Profiler tidak konsisten dengan temuan dari pengujian kinerja menggunakan JMeter, Kita dapat menggunakan teknik seperti menggunakan Docker daripada .jmx dan memperhatikan think time. 
Dengan cara ini, kita dapat meningkatkan konsistensi hasil pengujian JMeter dan mengurangi variasi antara mesin pengujian. Selain itu, juga penting untuk membandingkan hasil dari kedua alat tersebut (Jmeter & Intelij Profiler) untuk memperoleh pemahaman yang lebih baik tentang performa aplikasi dan penyebab perbedaan hasil.

   Ref: https://stackoverflow.com/questions/68666822/jmeter-results-not-consistent-and-depend-from-the-running-machine dan "gpt"


7. Apa yang saya lakukan sebelumnya adalah seperti setelah melakukan testing dan profiling, saya memperbaiki kode dengan memeriksa durasi program menggunakan JMeter. 
Jika terlalu lama, saya mengidentifikasi bagian kode yang menjadi masalah (ketidak-optimalan) dan mengoptimalkannya. 
Saya memastikan kebenaran perubahan dengan membandingkan outputnya dengan sebelumnya. Untuk lebih jauhnya, bisa juga kita lakukan dengan unit-testing untuk memastikan kebenaran code nya.

