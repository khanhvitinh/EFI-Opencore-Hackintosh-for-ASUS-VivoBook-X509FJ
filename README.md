# EFI-Opencore-Hackintosh-for-ASUS-VivoBook-X509FJ
Đây là EFI do mình tự Build, dành cho máy ASUS VivoBook model X509FJ. Thấy không ai sử dụng máy này Hackintosh nên mình tự build, có thể còn nhiều lỗi chưa được phát hiện và chưa được fix, nói chung mình là newbie mới tập hack nên không thể nào bằng các bác hackintosher lâu năm trong nghề được. Rất mong được mọi người giúp đỡ thêm để file EFI này hoàn chỉnh hơn.

Được build trên phiên bản mới nhất của OpenCore (0.8.6), mới nhất ở thời điểm hiện tại.
Bạn vui lòng vào phần Release để tải về nhé!

## Phiên bản OpenCore và phiên bản macOS đang sử dụng:

| OpenCore  | macOS   |
| --------  | ------- |
|   0.8.6 (mới nhất)  | Monterey 12.6.1 (Sử dụng SMBIOS ```MacBookPro15,2```) |

### Cảnh báo: Không nên dùng để cài bản macOS 13 Ventura vì kext Wi-Fi cho đến thời điểm hiện tại chưa có phiên bản tương tích.
#### Nếu sử dụng trên Big Sur, Catalina hoặc Mojave yêu cầu thay đổi kext Wi-Fi sao cho tương ứng với phiên bản macOS. Đối với Bluetooth thêm kext IntelBluetoothInjector.kext (do EFI này được build để cài đặt bản Monterey nên loại bỏ kext này do Apple viết lại cơ chế Bluetooth) và xóa kext BluetoothFixUp.kext.


</div>

## Cấu hình của Laptop:
 
Model laptop: ASUS VivoBook X509FJ (EJ227T).


CPU: Intel Core i3 8145U 2.3Ghz 2 nhân 4 luồng (dòng chipset Whiskey Lake, dựa trên Comet Lake) (hoạt động).


RAM: 4GB 2400Mhz (của Micron) (hoạt động).


GPU: 
- iGPU (card màn hình onboard): Intel UHD Graphics 620 (1GB VRAM) (hoạt động)
- dGPU (card màn hình rời): nVIDIA GeForce MX230 (chipset GP108, Pascal) (2GB VRAM), (không hoạt động, có thể web driver của nVIDIA hỗ trợ vì xài chipset hỗ trợ nhưng chắc cũng không cài được vì macOS không hỗ trợ Optimus như Windows, đã tắt bằng SSDT).

  
Ổ cứng: 
- HDD: Toshiba MQ04ABF100 (hoạt động, để chế độ AHCI, để theo cài đặt BIOS gốc để chế độ RAID thì không hoạt động.)
- 1 khe SSD M.2 (chưa gắn), cài qua ổ cứng ngoài (dùng đế cắm, cắm vào cổng USB 3.0). (Hoạt động).


Card Wi-Fi: Intel Wireless AC-9461 (hoạt động).


Card Bluetooth: sử dụng chung chipset Intel Wireless AC-9461 (hoạt động).


Card âm thanh: Realtek ALC256 (hoạt động tại layout-id 66, mic, tai nghe và loa ngoài tất cả đều nhận). Tai nghe nhận được thông qua bản vá SSDT.


Các cổng USB: 2 cổng USB phải (USB 2.0), 2 cổng USB trái (1 cổng USB 3.1 và 1 cổng Type C), riêng cổng Type C không hoạt động. 


Bàn di chuột: ELAN1200. (Hoạt động bình thường, cả khi sleep wake lại vẫn bình thường, 1 số bác report riêng loại chipset touchpad này dùng 1 lúc sẽ bị đơ nhưng mình không gặp hiện tượng đó, hoặc chưa có cơ duyên gặp :D).


Vân tay: ELAN WBF Fingerprint Sensor (không hoạt động).


Khe đọc thẻ nhớ Micro-SD: Realtek Card Reader USB 2.0 (hoạt động).


Camera: Realtek USB 2.0 VGA UVC WebCam (hoạt động).

## Tổng hợp lại các thứ hoạt động:
- CPU

- RAM

- iGPU (card màn hình onboard)

- Wi-Fi 

- Bluetooth

- Âm thanh

- USB (chỉ có 2 cổng USB và 1 cổng USB 3.1 nhận)

- Bàn di chuột 

- Khe đọc thẻ nhớ Micro SD.

- Camera.

- Cổng sạc.

- Chế độ ngủ (Sleep).

- Hàng phím chức năng.

- Restart / Shutdown.

## Tổng hợp các thứ không hoạt động:
- dGPU (card màn hình rời).

- Vân tay (nếu có ai fake được hệ thống Touch ID của Apple chắc may ra được).

- Phím khóa Function (tổ hợp phím Fn + Esc).

- Cổng USB Type C (đã map nhưng không nhận, chắc cần phải patch vá gì gì đó nó mới nhận).

- Phím nguồn (ấn nhưng không có tác dụng, chỉ có thể giữ để tắt nóng).

- Đèn nền bàn phím (dòng model này không có đèn nền).

- AirDrop và HandOff, cũng như Universal Control (cái này chắc có card native với realmac dùng được thôi, hi vọng sắp tới các bác hacker viết kext có thể port được chức năng này lên kext được thì bá đạo cmnl rồi, chắc người ta đổ xô ầm ầm bỏ Windows cài Hackintosh quá =)) dù sao cũng phải âm thầm cảm ơn các bác rất nhiều đã tận tụy phát triển nghiên cứu và giúp ích cho cộng đồng, viết chắc cũng không phải dễ đâu, phải gọi các bác làm thánh rồi, Tim Cook chắc cũng phải sợ các bác :D ). 

## Những thứ hoạt động không ổn định (có vấn đề) hoặc chưa được kiểm tra:

Chưa được kiểm tra:
- HDMI (chưa được kiểm tra và không biết có hoạt động không vì không có chỗ thử).

- Các ứng dụng iService (chưa được kiểm thử nên không biết có hoạt động không).

- Các tính năng phụ của macOS như BootCamp, Night Shift, FileVault,...

- Microphone ngoài theo cổng 3.5 (thấy có trong mục Audio mà không biết hoạt động không).

- SSD loại M.2, vì mình không có SSD M.2 cũng như điều kiện kinh tế chưa cho phép, bạn nào có máy cùng model giống mình mà có SSD M.2 có thể thử nhé, mình có bỏ vào kext NVMeFix dành cho những loại SSD không phải của Apple nên chắc chạy được, nhưng chưa kiểm tra nên cũng không chắc.

Hoạt động không ổn định:
- Quản lý năng lượng (Power Management), đã sử dụng kext CPUFriendDataProvider nhưng chắc config không chuẩn nên máy tuột pin rất nhanh so với Windows.

- Pin (tuột nhanh, có thể bị báo sai nữa, có lúc đang sạc mỗi lần khởi động lại máy lại báo mức pin khác nhau).

- Quạt tản nhiệt (mình không biết quạt tản nhiệt có hoạt động chính xác không, lúc mở máy thì máy nhanh nóng nhưng sau khi hoạt động được 1 lát thì nhiệt độ máy giảm xuống), có vẻ như quạt lúc quay yếu lúc quay mạnh.

- Màn hình (có vẻ màn hình tối hơn lúc máy chạy Windows, mình đã chỉnh đến độ sáng tối đa nhưng màn hình sáng (theo mình cảm nhận) chỉ bằng 80% lúc máy chạy hệ điều hành Windows).

- Wi-Fi: có lúc bị điên điên khùng khùng không kết nối được Wi-Fi, phải reset NVRAM hoặc boot lại qua Windows rồi trở lại Hackintosh thì may ra được.

- Bluetooth: kết nối với Bluetooth nếu không sử dụng ngay sau khi kết nối (chừng 15 - 30s), ví dụ như truyền file, xuất âm thanh ra loa Bluetooth thì nó sẽ tự ngắt kết nối (???)

- Âm thanh: nếu khởi động máy từ Windows trước, khi reboot lại chuyển qua macOS thì bị mất tiếng. Shutdown và boot trở lại vào macOS thì âm thanh hoạt động bình thường.


## Những thứ có vấn đề không biết sửa:
- Báo lỗi ACPI Error liên quan đến _UPC (AE_ALREADY_EXIST) trong chế độ Verbose Mode, hiện tại mình không biết fix làm sao hết, search google thì có vẻ cái này liên quan đến USB.

## Những điều cần lưu ý:
- Ở đây theo build gốc thì mình Build EFI OpenCore theo phiên bản macOS 12 Monterey, vì macOS Monterey được Apple viết lại cơ chế Injector Bluetooth, chi tiết ở đây:  [Link🔗](https://openintelwireless.github.io/IntelBluetoothFirmware/FAQ.html#what-additional-steps-should-i-do-to-make-bluetooth-work-on-macos-monterey-and-newer).
Do đó, nếu bạn muốn sử dụng EFI này trên phiên bản Big Sur thì cần phải tải file EFI dành cho Big Sur có chứa thêm kext Injector (Monterey trở lên không sử dụng kext này) và không có kext BluetoothFixUp (chỉ dùng cho Monterey trở lên vá lỗi Bluetooth cho card không phải của Apple).

- CẢNH BÁO: EFI này chưa được kiểm tra hoạt động trên macOS Big Sur (macOS 11), macOS Catalina (macOS 10.15) và Mojave (macOS 10.14), (phiên bản thấp nhất hỗ trợ chipset Comet Lake, Whiskey Lake dựa trên chipset này) nên mình không chắc chắn nó chạy được, mọi người có thể thử rồi report cho mình biết nha. EFI này chỉ được kiểm thử trên Monterey (macOS 12).

- CẢNH BÁO thứ 2: Không nên sử dụng EFI này để cài đặt macOS Ventura (macOS 13). Vì kext Wi-Fi của Intel chưa có cho bản Ventura (đang được thử nghiệm), nếu bạn cài sẽ bị tịt cái Wi-Fi, thiệt ra thì nó vẫn nhận Wi-Fi đó nhưng bạn kết nối máy sẽ bị treo cứng ngay lặp tức (có vẻ bị kernel panic, lỗi tương tự màn hình xanh chết chóc trên Windows). 

- Mình dùng USBToolBox, cũng có thể map không đúng nên nó không nhận USB Type C, hoặc phải patch cái gì thêm, nói chung mình là newbie nên không rành kakaka, bác nào rành giúp mình vụ này với, mình cảm ơn rất nhiều.

- Máy này tính ra hackintosh cấu hình dễ chịu đó các bạn, để mặc định hack luôn có kext sẵn hết không cần tháo thay gì hết kakaka, dĩ nhiên nếu các bạn thay sang card mà realmac dùng thì sẽ okay hơn nhưng thôi mình không muốn thay gì hết kakaka, thích chơi đồ nguyên bản thôi, chức năng phần cứng cũng hầu như nhận hết, thẻ nhớ cũng nhận luôn, bá vãi cả linh hồn, nhờ ông nào giúp được cái USB-C nữa thì máy này không khác gì realmac.

- Hàng phím chức năng bị đảo ngược, phải ấn Fn chung với chức năng được in trên phím, không như khi máy chạy Windows ấn trực tiếp phím để điều chỉnh chức năng, để sử dụng hàng phím Function thì làm thao tác ngược lại.

- Vì đây là file EFI đang pre-beta nên macOS chạy trên máy này khá nhiều lỗi và mình KHÔNG KHUYẾN KHÍCH các bạn sử dụng EFI này nếu bạn là người muốn sử dụng đồ có sẵn và lười tìm hiểu cách cài cũng như fix lỗi, vọc mò fix lỗi thì được kakaka, mình cũng người mới thôi, sau khi trải qua 7x7=49 lần thất bại đến tới đây bất lực quá nên mới cần nhờ cộng đồng giúp, nếu trong tương lai EFI này được cộng đồng giúp mình chỉnh sửa và hoạt động chạy okay hơn thì mọi người có thể tải về sử dụng nhé. Mình sẽ update theo thời gian khi rảnh.  

- Có thể ngoài những lỗi mình phát hiện và liệt kê ở trên còn có thể có những lỗi khác. Nếu các bạn phát hiện ra thì mời các bạn report cho mình biết nhé! Những lỗi nào đã được mình hoặc mọi người khắc phục thì mình sẽ gạch đi. Cảm ơn mọi người đã đọc!

## Sẽ còn update thêm...
