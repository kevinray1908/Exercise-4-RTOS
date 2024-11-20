# Exercise	4	-	Gain	a	good	understanding	of	task behaviour	where	a	priority	preemptive	scheduling	policy is	used.
Latihan ini bertujuan untuk memahami bagaimana sistem operasi real-time (RTOS) menangani multitasking dengan kebijakan penjadwalan preemptive priority. Anda akan mengamati bagaimana tugas-tugas dengan prioritas berbeda memengaruhi urutan eksekusi dalam sistem berbasis STM32 dan FreeRTOS.

## Tujuan
1. Memahami konsep preemptive scheduling di FreeRTOS.
2. Mengamati bagaimana prioritas tugas memengaruhi eksekusi dan interupsi antar tugas.
3. Mempraktikkan pembuatan tugas (task) dengan FreeRTOS pada STM32.

## Hardware Requirements
1. Board: STM32F4 Discovery Board (STM32F407G-DISC1).
2. Koneksi: Kabel USB untuk menyuplai daya dan memprogram board.

## Software Requirements
1. STM32CubeMX: Untuk konfigurasi proyek.
2. STM32CubeIDE atau Keil uVision: Untuk pengembangan dan kompilasi kode.
3. FreeRTOS Middleware: Terintegrasi melalui CubeMX.

## Langkah Implementasi
1. Konfigurasi STM32CubeMX: Pilih board STM32F103C
2. Aktifkan FreeRTOS dari tab Middleware.
3. Konfigurasikan GPIO untuk LED:
		GPIOA Pin 8: Red LED.
		GPIOA Pin 9: Green LED.
		GPIOA Pin 10: Orange LED (indikator tugas).
		GPIOA Pin 11: Blue LED (opsional untuk debugging).
		Generate kode untuk STM32CubeIDE atau Keil uVision.
5. Implementasi Kode Tugas: Tambahkan kode untuk tugas berikut:
		- Tugas 1 (Green LED):
			Prioritas: Normal.
			Berkedip 80 kali setiap 50 ms, diikuti dengan delay 6 detik.
		- Tugas 2 (Red LED):
			Prioritas: Above Normal.
			Berkedip 10 kali setiap 50 ms, diikuti dengan delay 1,5 detik.
			Gunakan fungsi FreeRTOS seperti osThreadNew() untuk membuat tugas dan vTaskDelay() untuk mengatur jeda.
6. Kompilasi dan Upload:
   Kompilasi kode menggunakan STM32CubeIDE atau Keil uVision.
   Flash ke board STM32.
7. Pengamatan: Perhatikan bagaimana Green LED berkedip lebih lambat dibanding Red LED. Red LED akan menginterupsi eksekusi Green LED karena memiliki prioritas lebih tinggi.

## Hasil yang Diharapkan
1. Green LED:
   Berkedip 80 kali setiap 50 ms, lalu delay 6 detik.
   Sering diinterupsi oleh Red LED, sehingga terlihat lebih lambat.
2. Red LED:
   Berkedip 10 kali setiap 50 ms, lalu delay 1,5 detik.
   Selalu memiliki prioritas lebih tinggi dibanding Green LED.
3. Indikator Blue/Orange LED:
   Blue LED menyala selama Green LED berjalan.
   Orange LED menyala selama Red LED berjalan.

## Troubleshooting
1. LED Tidak Menyala:
   Periksa konfigurasi GPIO di STM32CubeMX.
   Pastikan FreeRTOS diaktifkan dan thread dibuat dengan benar.
2. Red LED Tidak Menginterupsi Green LED:
   Periksa prioritas tugas di konfigurasi FreeRTOS.
   Pastikan prioritas red_Led Task lebih tinggi dari green_Led Task.

## Hasil Percobaan


https://github.com/user-attachments/assets/bdc883be-1eb5-43b1-bcfd-dbb7928ac774


