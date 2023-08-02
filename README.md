# EFI-Opencore-Hackintosh-for-ASUS-VivoBook-X509FJ
Đây là EFI do mình tự Build, dành cho máy ASUS VivoBook model X509FJ. Thấy không ai sử dụng máy này Hackintosh nên mình tự build, có thể còn nhiều lỗi chưa được phát hiện và chưa được fix, nói chung mình là newbie mới tập hack nên không thể nào bằng các bác hackintosher lâu năm trong nghề được. Rất mong được mọi người giúp đỡ thêm để file EFI này hoàn chỉnh hơn.

Được build trên phiên bản mới nhất của OpenCore (0.9.3), mới nhất ở thời điểm hiện tại.
Bạn vui lòng vào phần Release để tải về nhé!

## Phiên bản OpenCore và phiên bản macOS đang sử dụng:

| OpenCore  | macOS   |
| --------  | ------- |
|   0.9.3 (mới nhất)  | Ventura 13.5 (Sử dụng SMBIOS ```MacBookPro15,2```) |

### Cảnh báo: EFI này không nên sử dụng để cài đặt macOS Sonoma (macOS 14). Nếu cài, bạn sẽ mất Wi-Fi (Bluetooth vẫn hoạt động bình thường ???). Để có thể sử dụng được Wi-Fi, vui lòng đọc mục "Những điều cần lưu ý" ở dưới. Cảm ơn bạn! 


</div>

## Cấu hình của Laptop:
 
Model laptop: ASUS VivoBook X509FJ (EJ227T).


CPU: Intel Core i3 8145U 2.3Ghz 2 nhân 4 luồng (dòng chipset Whiskey Lake, dựa trên Comet Lake) (hoạt động).


RAM: 12GB 2400Mhz (của Micron) (hoạt động).


GPU: 
- iGPU (card màn hình onboard): Intel UHD Graphics 620 (2GB VRAM), (hoạt động)
- dGPU (card màn hình rời): nVIDIA GeForce MX230 (chipset GP108, Pascal) (2GB VRAM), (không hoạt động)

  
Ổ cứng: 
- Khe SATA: Samsung EVO 860 500GB (hoạt động, để chế độ AHCI, để theo cài đặt BIOS gốc ở chế độ RAID thì không hoạt động.)
- Khe PCIe: Sabrent Rocket NVMe 256GB (Hoạt động).


Card Wi-Fi: Intel Wireless AC-9461 (hoạt động).


Card Bluetooth: sử dụng chung chipset Intel Wireless AC-9461 (hoạt động).


Card âm thanh: Realtek ALC256 (hoạt động tại layout-id 66, mic, tai nghe và loa ngoài tất cả đều nhận).


Các cổng USB: 2 cổng USB phải (USB 2.0), 2 cổng USB trái (1 cổng USB 3.1 và 1 cổng Type C), riêng cổng Type C chỉ hoạt động khi bạn cắm usb trước khi bật máy. Sau khi boot vào macOS thì cắm nó sẽ không nhận (Không có khả năng cắm nóng - hiện tại chưa fix được). 


Bàn di chuột: ELAN1200. (Hoạt động bình thường, cả khi sleep wake lại vẫn bình thường, 1 số bác report riêng loại chipset touchpad này dùng 1 lúc sẽ bị đơ nhưng mình không gặp hiện tượng đó, hoặc chưa có cơ duyên gặp :D).


Vân tay: ELAN WBF Fingerprint Sensor (không hoạt động).


Khe đọc thẻ nhớ Micro-SD: Realtek Card Reader USB 2.0 (hoạt động).


Camera: Realtek USB 2.0 VGA UVC WebCam (hoạt động).

## Tổng hợp lại các thứ hoạt động:
- CPU.

- RAM.

- iGPU (card màn hình onboard).

- Wi-Fi.

- Bluetooth.

- Âm thanh.

- USB (Riêng USB Type C phải cắm trước khi boot vào macOS thì mới nhận).

- Bàn di chuột (đa điểm).

- Khe đọc thẻ nhớ Micro SD.

- Camera.

- Cổng sạc.

- SSD (PCIe và SATA).

- Chế độ ngủ (Sleep).

- Hàng phím chức năng.

- Restart / Shutdown.

- HDMI (chỉ 4K 30Hz).

- Các ứng dụng iService (Đăng nhập Apple ID như bình thường).

- Các tính năng phụ của macOS như BootCamp, Night Shift, FileVault,...

## Tổng hợp các thứ không hoạt động:
- dGPU (card màn hình rời).

- Vân tay (nếu có ai fake được hệ thống Touch ID của Apple chắc may ra được).

- Phím khóa Function (tổ hợp phím Fn + Esc).

- Đèn nền bàn phím (dòng model này không có đèn nền).

- AirDrop và HandOff, cũng như Universal Control (cái này chắc có card native với realmac dùng được thôi, hi vọng sắp tới các bác hacker viết kext có thể port được chức năng này lên kext được thì bá đạo cmnl rồi, chắc người ta đổ xô ầm ầm bỏ Windows cài Hackintosh quá =)) dù sao cũng phải âm thầm cảm ơn các bác rất nhiều đã tận tụy phát triển nghiên cứu và giúp ích cho cộng đồng, viết chắc cũng không phải dễ đâu, phải gọi các bác làm thánh rồi, Tim Cook chắc cũng phải sợ các bác :D ). 

## Những thứ hoạt động không ổn định (có vấn đề) hoặc chưa được kiểm tra:

Chưa được kiểm tra:

Hoạt động không ổn định:
- Quản lý năng lượng (Power Management), pin tuột nhanh hơn so với dùng Windows.

- Pin (tuột nhanh, có thể bị báo sai nữa, có lúc đang sạc mỗi lần khởi động lại máy lại báo mức pin khác nhau).

- Quạt tản nhiệt (mình không biết quạt tản nhiệt có hoạt động chính xác không, lúc mở máy thì máy nhanh nóng nhưng sau khi hoạt động được 1 lát thì nhiệt độ máy giảm xuống), có vẻ như quạt lúc quay yếu lúc quay mạnh.

- Màn hình (có vẻ màn hình tối hơn lúc máy chạy Windows, mình đã chỉnh đến độ sáng tối đa nhưng màn hình sáng (theo mình cảm nhận) chỉ bằng 80% lúc máy chạy hệ điều hành Windows).

- Wi-Fi: có lúc bị điên điên khùng khùng không kết nối được Wi-Fi, phải reset NVRAM hoặc boot lại qua Windows rồi trở lại Hackintosh thì may ra được. Đối với Ventura khi boot vào bộ cài online có khi không bật sẵn Wi-Fi mà cần tự bật. Các phiên bản khác không gặp vấn đề này. Các phiên bản Catalina trở xuống khi boot vào macOS thì OpenCore gặp bug không tiêm được kext vào hệ thống macOS. Về vấn đề này để khắc phục bạn vui lòng xem ở dưới.

- Âm thanh: nếu khởi động máy từ Windows trước, khi reboot lại chuyển qua macOS thì bị mất tiếng. Full Shutdown và boot trở lại vào macOS thì âm thanh hoạt động bình thường. 

- HDMI: không xuất được màn hình ở độ phân giải 4K 60Hz. Chỉ hoạt động ở 4K 30Hz. Mình đang tìm hiểu cách vá lỗi.

## Những thứ có vấn đề không biết sửa:
- Báo lỗi ACPI Error liên quan đến _UPC (AE_ALREADY_EXIST) trong chế độ Verbose Mode, hiện tại mình không biết fix làm sao hết vì không chuyên sâu về SSDT, search google thì có vẻ cái này liên quan đến USB.

## Những thứ vừa sửa được qua bản cập nhật:
- HDMI (tuy nhiên không hoạt động với 4K 60Hz).
- Cổng âm thanh 3.5.
- USB Type C (tuy nhiên cần cắm trước khi boot vào macOS).
- Bật hiệu ứng đèn nền giúp tăng giảm độ sáng mượt mà hơn (Như Windows).
- Đã thêm thuộc tính sửa lỗi cho thông tin card màn hình onboard nhằm sửa lỗi màn hình đen trên macOS Ventura. 
- Bluetooth (tương đối hoạt động đã ổn định). Đã tùy biến kext Bluetooth có thể cài đặt trên tất cả phiên bản macOS từ High Sierra cho đến Ventura (hiện tại). Bạn không cần chỉnh sửa lại EFI để thêm kext nữa.
- Đã thêm hỗ trợ Wi-Fi trên Ventura.
- Có thể sử dụng EFI này trên nhiều phiên bản Windows từ High Sierra cho đên Ventura (hiện tại).
- Đã kiểm tra và cổng ổ cứng PCIe NVMe hoạt động bình thường.
  
## Những điều cần lưu ý:
- EFI này có thể sử dụng cho phiên bản macOS mới nhất Ventura và bản Sonoma beta. Tuy nhiên, khi cài đặt thì Wi-Fi trên Sonoma sẽ không thể sử dụng được (mặc dù OpenCore không báo tiêm kext thất bại). Bạn có thể sử dụng giải pháp kext Itlwm cùng với app HeliPort để thay thế.

**- CẢNH BÁO: Wi-Fi từ High Sierra đến Ventura hoạt động ổn định. Tuy nhiên, OpenCore gặp 1 lỗi bug đối với Catalina trở xuống, kext Wi-Fi chỉ nhúng được vào trong bộ cài. Khi boot vào trong macOS thì OpenCore gặp bug không tiêm được Kext vào hệ thống macOS. Giải pháp cho vấn đề này thì bạn sẽ cần dùng Kext Droplet để cài đặt kext Wi-Fi từ EFI vào thẳng hệ thống macOS thì Wi-Fi sẽ hoạt động bình thường. [Link🔗](https://github.com/chris1111/Kext-Droplet/releases/tag/V2)**

**- CẢNH BÁO 2: Nếu dùng EFI này để cài macOS High Sierra, bạn cần có bộ cài macOS High Sierra 10.13.6 có tích hợp bản cập nhật bổ sung dành cho kiểu máy MacBook Pro 2018 (mã build 17G2112). Đa phần các bộ cài macOS High Siera trên mạng đều là bản cũ hoặc thấp hơn version này nên khi bạn boot vào sẽ xảy ra một trong hai lỗi như sau:**

  ![image](https://github.com/khanhvitinh/EFI-Opencore-Hackintosh-for-ASUS-VivoBook-X509FJ/assets/110464941/237ec57f-44d4-43db-a3ae-e379c9914247)
_Lỗi cấm đi ngược chiều huyền thoại trên macOS khi bộ cài không tương tích hoặc database có trong bộ cài không hỗ trợ kiểu máy Mac (xuất hiện khi boot không verbose)_


![image](https://github.com/khanhvitinh/EFI-Opencore-Hackintosh-for-ASUS-VivoBook-X509FJ/assets/110464941/cde0a33c-03b3-431b-812a-db0f3ebdd2be)
_Lỗi khi bộ cài kiểm tra SMBIOS và phát hiện SMBIOS không có trong database của bộ cài nên chặn không cho boot (chỉ xuất hiện khi boot verbose)_


_**Để vượt lỗi này, bạn có 2 phương pháp:**_

**_- Phương pháp 1: Bạn cần một máy hackintosh hoặc máy Mac khác tải bộ cài High Sierra từ App Store và write ra usb để cài. Cái này hơi bất tiện nhưng là phương pháp tối ưu nhất vì bộ cài từ App Store luôn là bản mới nhất._**

**_- Phương pháp 2: Vượt lỗi check SMBIOS bằng cách ấn tổ hợp phím Command + C và Minus (phím dấu trừ) khi đang ở trong màn hình Menu Boot của OpenCore (đối với laptop này là phím Windows + C và dấu trừ) hoặc thêm boot-args -no_compat_check trong file config.plist của EFI này._**

_Phương pháp này không tối ưu và không phải lúc nào cũng thành công, nếu phiên bản bộ cài quá xa với phiên bản được yêu cầu như trên (như 10.13.5 trở xuống thì có thể không khởi động được và sẽ bị treo). Đối với bộ cài online tải từ hướng dẫn tạo EFI OpenCore trên trang Dortania thì cách này thực hiện được. Sau khi cài đặt thành công, bạn có thể cần cài bản cập nhật bổ sung 1 và 2 để có thể điều chỉnh được độ sáng và hệ thống hoạt động ổn định._  

Bản cập nhật số 1: [Link🔗](https://support.apple.com/kb/DL1973)
Bản cập nhật số 2: [Link🔗](https://support.apple.com/kb/DL1974)

Trong tương lai nếu các phiên bản macOS sau không còn hỗ trợ SMBIOS MacBook Pro 2018 nữa thì chúng ta cũng có thể áp dụng cách như trên để vượt lỗi và cài đặt.

- Máy này tính ra hackintosh cấu hình dễ chịu đó các bạn, để mặc định hack luôn có kext sẵn hết không cần tháo thay gì hết kakaka, dĩ nhiên nếu các bạn thay sang card mà realmac dùng thì sẽ okay hơn nhưng thôi mình không muốn thay gì hết kakaka, thích chơi đồ nguyên bản thôi, chức năng phần cứng cũng hầu như nhận hết, thẻ nhớ cũng nhận luôn, bá vãi cả linh hồn, nhờ ông nào giúp được cái USB-C nữa thì máy này không khác gì realmac.

- Hàng phím chức năng bị đảo ngược, phải ấn Fn chung với chức năng được in trên phím, không như khi máy chạy Windows ấn trực tiếp phím để điều chỉnh chức năng, để sử dụng hàng phím Function thì làm thao tác ngược lại.

- Để cài đặt trên SSD NVMe thì bạn cần bảo đảm là SSD NVMe đó tương tích. Một số mẫu laptop ASUS này có sử dụng ổ cứng Intel SSD NVMe thì có thể cài đặt được nhưng hên xui có thể gặp lỗi. Nếu là SSD khác thì có thể sẽ gặp lỗi khi boot macOS, trường hợp này bạn muốn cài lên ổ cứng SATA trong máy hoặc ổ cứng ngoài thì bạn cần chỉnh sửa config.plist trong EFI, kiếm dòng boot-args và thêm nvme=-1 vào cuối dòng boot-args. Tùy chọn này sẽ ẩn ổ cứng NVMe trong máy của bạn làm cho macOS không nhìn thấy nó và không xảy ra xung đột gây lỗi khởi động mà không cần tháo ra. Còn model máy mình không có sẵn SSD NVMe nên mình đã mua 1 SSD tương tích hoàn hảo để gắn và chạy rất tốt.

- Vì đây là file EFI đang pre-beta nên macOS chạy trên máy này khá nhiều lỗi và mình KHÔNG KHUYẾN KHÍCH các bạn sử dụng EFI này nếu bạn là người muốn sử dụng đồ có sẵn và lười tìm hiểu cách cài cũng như fix lỗi, vọc mò fix lỗi thì được kakaka, mình cũng người mới thôi, sau khi trải qua 7x7=49 lần thất bại đến tới đây bất lực quá nên mới cần nhờ cộng đồng giúp, nếu trong tương lai EFI này được cộng đồng giúp mình chỉnh sửa và hoạt động chạy okay hơn thì mọi người có thể tải về sử dụng nhé. Mình sẽ update theo thời gian khi rảnh.  

- Có thể ngoài những lỗi mình phát hiện và liệt kê ở trên còn có thể có những lỗi khác. Nếu các bạn phát hiện ra thì mời các bạn report cho mình biết nhé! Những lỗi nào đã được mình hoặc mọi người khắc phục thì mình sẽ gạch đi. Cảm ơn mọi người đã đọc!

## Sẽ còn update thêm...
