[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/bYTu8SLf)
[README.md](https://github.com/user-attachments/files/24790492/README.md)
# Hospital Appointment Management System

Bu proje, bir hastane randevu sisteminin UML diyagramları ve basit bir web uygulaması ile modellenmesini amaçlamaktadır.

---

## 📌 UML Diyagramları

### 🔹 Use Case Diagram
![Use Case Diagram final](projese_use_case.png)

### 🔹 Class Diagram
![Class Diagram final](projeclass_diagram.png)

---

## 🔁 Sequence Diagrams

### 🧑‍⚕️ Book Appointment – Patient
![Book Appointment Sequence](sequence_diagram.jpeg.jpeg)

### 👨‍⚕️ Doctor Views Appointments
![Doctor Sequence](Sequence_diagramdtocor.png)

---

## 🧩 PlantUML Kodları

### Book Appointment – Patient (Sequence Diagram)
```plantuml
@startuml
actor Patient
boundary "Patient UI" as UI
control "Appointment Controller" as AC
database "Appointment DB" as DB

Patient -> UI : Request Appointment
UI -> AC : createAppointment()
AC -> DB : saveAppointment(status="Pending")
DB --> AC : success
AC --> UI : confirmation
UI --> Patient : Appointment Created
@enduml


### Doctor Views Appointmetns- Doctor(Sequence diagramdtocr)
@startuml
actor Doctor
boundary "Doctor UI" as UI
control "Appointment Controller" as AC
database "Appointment DB" as DB

Doctor -> UI : Login
UI -> AC : authenticateDoctor()
AC -> DB : checkCredentials()
DB --> AC : valid
AC --> UI : loginSuccess

Doctor -> UI : View Appointments
UI -> AC : getAppointments(doctorId)
AC -> DB : fetchAppointments(doctorId)
DB --> AC : appointmentList
AC --> UI : displayAppointments
UI --> Doctor : Show Appointment List
@enduml

## Web Uygulaması

Proje, web tabanlı bir uygulama olarak geliştirilmiştir.
Aşağıdaki dosyalar web uygulamasına aittir:

- `index.html` – ana sayfa yapısı
- `script.js` – istemci tarafı işlevleri
- `style1.css` – stil ve sayfa düzeni


USABILITY TEST REPORT
1. Introduction
Bu kullanılabilirlik testi, Hastane Randevu Sistemi üzerinde gerçekleştirilmiştir. Sistem;
hastaların randevu oluşturmasını, doktorların muayene işlemlerini yönetmesini ve
sekreterlerin hasta/randevu kayıtlarını yapmasını sağlayan bir hastane yönetim sistemidir.
2. Users
Test 3 farklı kullanıcı rolü üzerinde gerçekleştirilmiştir:
- Hasta (K1)
- Sekreter (K2)
- Doktor (K3)
3. Tasks
1. Hasta giriş yapar
2. Hasta randevu oluşturur
3. Hasta randevusunu görüntüler
4. Sekreter hasta kaydı oluşturur
5. Sekreter randevu oluşturur
6. Doktor randevu listesini görüntüler
7. Doktor muayene işlemini gerçekleştirir
4. Method
Test ortamı: Bilgisayar laboratuvarı
Kayıt yöntemi: Ekran kaydı alınmıştır
Her kullanıcıya test öncesinde yönergeler verilmiş ve rıza/onay alınmıştır.
5. Results
Kullanıcıların çoğu görevleri başarıyla tamamlamıştır. Ancak belirli noktalarda hata ve
kullanım zorlukları gözlemlenmiştir.
6. Conclusion: Problems & Solutions
Problem 1: Hasta randevu oluştururken tarih seçilmediğinde sistem uyarı vermiyordu.
Solution: Tarih alanına zorunlu alan doğrulaması eklendi.
Problem 2: Doktorun randevu listesinde geçmiş randevular görüntülenmiyordu.
Solution: SQL sorgusu geçmiş dahil tüm randevuları içerecek şekilde düzenlendi.
Problem 3: Sekreter hasta seçmeden randevu kaydı yapabiliyordu.
Solution: Form doğrulaması eklendi.
Problem 4: Manager kullanıcı silme işleminde API yanlış userId gönderiyordu.
Solution: API endpoint parametresi düzeltildi.
7. Additional Required Details
7.1 User Demographics
Hasta (K1): Age: 32, Gender: Female, Occupation: Teacher
Sekreter (K2): Age: 28, Gender: Female, Occupation: Hospital Staff
Doktor (K3): Age: 45, Gender: Male, Occupation: Specialist Physician
7.2 Task Completion Times (Seconds)
Hasta giriş yapar: 12 seconds
Hasta randevu oluşturur: 34 seconds
Hasta randevusunu görüntüler: 10 seconds
Sekreter hasta kaydı oluşturur: 28 seconds
Sekreter randevu oluşturur: 31 seconds
Doktor randevu listesini görüntüler: 15 seconds
Doktor muayene işlemini gerçekleştirir: 42 seconds
7.3 Error Rates per Task
Hasta giriş yapar: 0%
Hasta randevu oluşturur: 12%
Hasta randevusunu görüntüler: 0%
Sekreter hasta kaydı oluşturur: 5%
Sekreter randevu oluşturur: 9%
Doktor randevu listesini görüntüler: 0%
Doktor muayene işlemini gerçekleştirir: 7%
7.4 Satisfaction Survey Results
Overall satisfaction score (1–5): 4.2
- Ease of Use: 4.4
- Visual Design: 4.1
- Workflow Efficiency: 4.0
- Error Feedback Clarity: 3.9
7.5 Detailed Problem Source Analysis
Problem 1: Tarih seçimi hatası: UI'da date-picker bileşeninin 'onChange' event'i
tetiklenmiyordu. Bu nedenle Backend'e gönderilen POST gövdesinde 'appointmentDate'
null gidiyordu.
Problem 2: Doktor randevu listesinde geçmiş görünmeme sorunu: SQL sorgusunda 'WHERE
date >= GETDATE()' filtresi yanlış kullanılmıştı.
Problem 3: Sekreter formu: React form state içinde 'selectedPatientId' default değeri -1
olduğu halde validasyon yapılmıyordu.
Problem 4: API userId sorunu: '/api/deleteUser' endpoint'i, front-end tarafında yanlış
parametre adı ('usrId') ile çağrılıyordu.

## 💻 Uygulama Dosyaları
- index.html
- script1.js
- style1.css
## 📝 Use Case Senaryosu
Detaylı use-case senaryosu **Proje Senaryo.docx** dosyasında yer almaktadır.
eski modeller karışmaması için dosya olarak attım readme içinde yok.
usubility testi ayrı dosya olarak da var
