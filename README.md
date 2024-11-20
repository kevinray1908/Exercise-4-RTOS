Deskripsi
Latihan ini bertujuan untuk memahami bagaimana sistem operasi real-time (RTOS) menangani multitasking dengan kebijakan penjadwalan preemptive priority. Anda akan mengamati bagaimana tugas-tugas dengan prioritas berbeda memengaruhi urutan eksekusi dalam sistem berbasis STM32 dan FreeRTOS.

Tujuan
Memahami konsep preemptive scheduling di FreeRTOS.
Mengamati bagaimana prioritas tugas memengaruhi eksekusi dan interupsi antar tugas.
Mempraktikkan pembuatan tugas (task) dengan FreeRTOS pada STM32.
Hardware Requirements
Board: STM32F4 Discovery Board (STM32F407G-DISC1).
Koneksi: Kabel USB untuk menyuplai daya dan memprogram board.
Software Requirements
STM32CubeMX: Untuk konfigurasi proyek.
STM32CubeIDE atau Keil uVision: Untuk pengembangan dan kompilasi kode.
FreeRTOS Middleware: Terintegrasi melalui CubeMX.
Langkah Implementasi
Konfigurasi STM32CubeMX:

Pilih board STM32F407G-DISC1.
Aktifkan FreeRTOS dari tab Middleware.
Konfigurasikan GPIO untuk LED:
GPIOA Pin 8: Red LED.
GPIOA Pin 9: Green LED.
GPIOA Pin 10: Orange LED (indikator tugas).
GPIOA Pin 11: Blue LED (opsional untuk debugging).
Generate kode untuk STM32CubeIDE atau Keil uVision.
Implementasi Kode Tugas: Tambahkan kode untuk tugas berikut:

Tugas 1 (Green LED):
Prioritas: Normal.
Berkedip 80 kali setiap 50 ms, diikuti dengan delay 6 detik.
Tugas 2 (Red LED):
Prioritas: Above Normal.
Berkedip 10 kali setiap 50 ms, diikuti dengan delay 1,5 detik.
Gunakan fungsi FreeRTOS seperti osThreadNew() untuk membuat tugas dan vTaskDelay() untuk mengatur jeda.

Kompilasi dan Upload:

Kompilasi kode menggunakan STM32CubeIDE atau Keil uVision.
Flash ke board STM32.
Pengamatan:

Perhatikan bagaimana Green LED berkedip lebih lambat dibanding Red LED.
Red LED akan menginterupsi eksekusi Green LED karena memiliki prioritas lebih tinggi.
