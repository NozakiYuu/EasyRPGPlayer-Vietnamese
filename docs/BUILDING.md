# Tài liệu dành cho xây dựng

## Các thư viện

Nếu hệ điều hành của bạn có một trình quản lý thư viện thì hãy sử dụng nó để cài đặt các thư viện, ví dụ như [vcpkg](https://github.com/Microsoft/vcpkg) ở trên Windows hoặc [Advanced Packaging Tool](https://wiki.debian.org/Apt) (apt) ở trên Ubuntu.

Trong trường hợp bạn muốn tự xây dựng các thư viện đó thì bạn có thể tham khảo script xây dựng các thư viện (trừ thư viện [liblcf], bằng tiếng Anh) tại trang [buildscripts] của EasyRPG.


## Xây dựng ứng dụng trên Linux

### Sử dụng Autotools (Makefile)

Phương thức xây dựng này đã được thử nghiệm thành công bởi nhà phát triển của bản tiếng Việt.

Yêu cầu các thư viện được đề cập ở phần [README](/README.md), phần *Các thư viện* ở bên trên và các ứng dụng sau:

- pkg-config
- GNU make

Nếu bạn xây dựng ứng dụng từ mã nguồn có sẵn trên GitHub, bạn cần sử dụng thêm các ứng dụng này:

- autoconf >= 2.69
- automake >= 1.11.4
- libtool

**Hướng dẫn chi tiết:**

Mở ứng dụng Dòng lệnh (Terminal) ở trên máy tính của bạn và chạy các câu lệnh sau:

    cd EasyRPGPlayer-Vietnamese      # Truy cập vào thư mục chứa mã nguồn
	autoreconf -i                    # Cài đặt trước khi tìm thư viện
    ./configure                      # Tìm thư viện và cài đặt trước khi xây dựng
    make                             # Biên dịch và xây dụng ứng dụng
	
Sau khi xây dựng, một tệp tin `easyrpg-player` sẽ xuất hiện ở thư mục chứa mã nguồn. Đây là tệp tin ứng dụng dùng để gỡ lỗi và không nên sử dụng để chia sẻ lên công khai.

### Sử dụng CMake

Phương thức xây dựng này đã được thử nghiệm thành công bởi nhà phát triển của bản tiếng Việt.

Yêu cầu các thư viện được đề cập ở phần [README](/README.md), phần *Các thư viện* ở bên trên và các ứng dụng sau:

- pkg-config (chỉ ở trên Linux)
- CMake 3.10 hoặc cao hơn

**Hướng dẫn chi tiết:**

Mở ứng dụng Dòng lệnh (Terminal) ở trên máy tính của bạn và chạy các câu lệnh sau:

    cd EasyRPGPlayer-Vietnamese           # Truy cập vào thư mục chứa mã nguồn
    cmake . -DCMAKE_BUILD_TYPE=Release    # Tìm thư viện và cài đặt trước khi xây dựng
    cmake --build .                       # Biên dịch và xây dựng ứng dụng
    sudo cmake --build . --target install # Cài đặt ứng dụng trên toàn bộ hệ thống của hệ điều hành
    
Nếu bạn bị lỗi thư viện (`Cannot find -lgrm`), bạn có thể dùng lệnh sau để cài thư viện:

    sudo apt-get install --install-recommends libdrm-dev libgbm1 libgbm-dev libdecor-0-dev
    
Sau khi xây dựng, một tệp tin `easyrpg-player` sẽ xuất hiện ở thư mục chứa mã nguồn.
	
## Windows

Ở trên Windows, cách duy nhất để xây dựng ứng dụng Player là sử dụng CMake và Visual Studio. Cách xây dựng gốc của EasyRPG có thể sẽ có lỗi phát sinh, nên đây là cách xây dựng tốt nhất được nghĩ ra bởi Nozaki Yuu và [toaranotdev](https://github.com/toaranotdev):

Yêu cầu các ứng dụng sau trước khi bắt đầu xây dựng:

- CMake 3.10 hoặc cao hơn
- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/older-downloads) hoặc cao hơn
- [Git](https://git-scm.com/download/win)

**Hướng dẫn chi tiết:**

### Xây dựng thư viện

Mở Command Prompt (Dấu nhắc lệnh) và dùng lệnh `cd` để trỏ tới thư mục bạn muốn. Sau đó sử dụng các câu lệnh sau:

	git clone https://github.com/EasyRPG/buildscripts.git       # Tải công cụ xây dựng thư viện của EasyRPG
	cd buildscripts\windows                                     # Trỏ tới thư mục xây dựng thư viện trên Windows
	.\build                                                     # Bắt đầu xây dựng thư viện trên Windows
	vcpkg integrate install                                     # Liên kết vcpkg với CMake
	
Nếu thời gian xây dựng của bạn quá lâu, bạn cũng có thể tải thư viện đã được xây dựng sẵn tại trang web https://ci.easyrpg.org/view/Windows/job/toolchain-windows và giải nén nó vào thư mục của vcpkg.
	
Sau khi thực hiện các câu lệnh trên, các thư viện được yêu cầu đã được cài đặt và đã sẵn sàng để thêm vào CMake.

Hãy nhớ thư mục của vcpkg vì bạn sẽ cần sử dụng nó để thực hiện các lệnh ở bên dưới. Dùng lệnh `cd` để trỏ tới thư mục chứa mã nguồn.

### Cài đặt dự án

Thực hiện các lệnh sau tuỳ theo phiên bản Player mà bạn muốn xây dựng.

#### Bản 32-bit:

	cmake . -DSHARED_RUNTIME=OFF -DVCPKG_TARGET_TRIPLET=x86-windows-static -DCMAKE_TOOLCHAIN_FILE=(đường dẫn vcpkg)\scripts\buildsystems\vcpkg.cmake
	-DCMAKE_BUILD_TYPE=(loại xây dựng) -DPLAYER_BUILD_LIBLCF=ON -A Win32
	
Trong đó, `(đường dẫn vcpkg)` là đường dẫn thư mục của vcpkg đã làm ở bước trên, còn `(loại xây dựng)` có thể là `Debug`, `Release` hoặc `RelWithDebInfo` tuỳ theo mục đích sử dụng của bạn.

Khi đó, dự án để xây dựng Player sẽ được cài đặt. Tuy nhiên ở một số máy có thể sẽ bị lỗi thư viện fmt, khi đó bạn hãy dùng một trình chỉnh sửa (ví dụ như Notepad) và mở tệp tin sau:

	(đường dẫn vcpkg)\installed\x86-windows-static\share\fmt\fmt-config-version.cmake
	
Và xoá dòng `set(PACKAGE_VERSION_UNSUITABLE TRUE)`. Sau đó hãy thực hiện lại lệnh trên và dự án bây giờ đã có thể cài đặt được bình thường.

#### Bản 64-bit:

Bản 64-bit chỉ có thể được xây dựng khi bạn đang sử dụng Windows bản 64-bit.

	cmake . -DSHARED_RUNTIME=OFF -DVCPKG_TARGET_TRIPLET=x64-windows-static -DCMAKE_TOOLCHAIN_FILE=(đường dẫn vcpkg)\scripts\buildsystems\vcpkg.cmake
	-DCMAKE_BUILD_TYPE=(loại xây dựng) -DPLAYER_BUILD_LIBLCF=ON -A x64
	
Trong đó, `(đường dẫn vcpkg)` là đường dẫn thư mục của vcpkg đã làm ở bước trên, còn `(loại xây dựng)` có thể là `Debug`, `Release` hoặc `RelWithDebInfo` tuỳ theo mục đích sử dụng của bạn.
	
Sau đó dự án sẽ được cài đặt bình thường và không có lỗi nào xảy ra cả.

Lưu ý rằng nếu bạn chuyển đổi cài đặt giữa bản 32-bit và bản 64-bit, bạn cần xoá thư mục `CMakeFiles` và tệp tin `CMakeCache.txt`.

### Xây dựng ứng dụng

Sau khi làm tất cả các bước trên, mở tệp tin `EasyRPG_Player.sln` bằng Visual Studio bản 2019 hoặc cao hơn, thay đổi Build Type thành `Debug`, `Release` hoặc `RelWithDebInfo` tuỳ theo mục đích sử dụng của bạn và nhấn nút `Build -> Build Solution` (hoặc tổ hợp `Ctrl + Shift + B`).

Bạn cũng có thể xây dựng bằng cách dùng lệnh sau:

	cmake --build .
	
nhưng lỗi `Debug Assertion Error` khi chạy ứng dụng sẽ có thể xảy ra. Nên dùng Visual Studio để xây dựng như ở cách trên.

Sau khi xây dựng xong, một tệp tin `Player.exe` sẽ xuất hiện ở thư mục `Debug`, `Release` hoặc `RelWithDebInfo` tuỳ theo Build Type mà bạn đã chọn.

## Android

Phương thức này chưa được thử nghiệm và có thể sẽ có lỗi phát sinh.

Khuyên dùng hệ điều hành Linux để thực hiện việc xây dựng, vì Windows có thể sẽ có lỗi trong quá trình xây dựng thư viện.

Mở Terminal (Dòng lệnh) và chạy các câu lệnh sau:

	git clone https://github.com/EasyRPG/buildscripts.git       # Tải công cụ xây dựng thư viện của EasyRPG
	cd buildscripts/android                                     # Trỏ tới thư mục xây dựng thư viện trên Android
	
Tạo một KeyStore bằng Android Studio hoặc KeyStore Manager. Hướng dẫn tạo thì bạn có thể tìm hiểu ở trên Google.

Dùng một trình chỉnh sửa văn bản (như Notepad) để mở tệp tin sau:

	buildscripts/android/5_build_android_port.sh
	
Chỉnh sửa 3 biến sau ở trong tệp tin:

- `KEYSTORE_PATH` = đường dẫn chứa tệp tin KeyStore mà bạn đã tạo ở bước trên
- `KEYSTORE_PASSWORD` = mật khẩu của tệp tin KeyStore mà bạn đã nhập trong lúc tạo
- `KEYSTORE_NAME` = tên của KeyStore, bạn có thể nhập tên bất kì nhưng không được chứa dấu cách

Thay đổi dòng sau trong tệp tin:

    if [ ! -d Player/.git ]; then
        git clone https://github.com/EasyRPG/Player.git
    
thành:

    if [ ! -d EasyRPGPlayer-Vietnamese/.git ]; then
        git clone https://github.com/NozakiYuu/EasyRPGPlayer-Vietnamese.git
    
Và thay đổi dòng sau:

    cd Player/builds/android
    
thành:

    cd EasyRPGPlayer-Vietnamese/builds/android

Sau đó, chạy dòng lệnh sau ở cửa sổ dòng lệnh đang mở ở bước trên.

	./0_build_everything.sh
	
Và đợi cho EasyRPG Player trên Android được xây dựng xong. Nếu có lỗi thư viện (`Cannot find -l<tên thư viện>`) bạn có thể cài đặt thư viện đó và chạy lại lệnh:

	./5_build_android_port.sh
	

## Hệ điều hành khác

Để xem cách xây dựng cho các hệ điều hành khác, bạn có thể tham khảo [hướng dẫn xây dựng bằng tiếng Anh](https://github.com/EasyRPG/Player/blob/master/docs/BUILDING.md). Các cách ở trong trang đó vẫn chưa được thử nghiệm bởi nhà phát triển bản tiếng Việt nên có thể sẽ có lỗi phát sinh.

[buildscripts]: https://github.com/EasyRPG/buildscripts
[liblcf]: https://github.com/EasyRPG/liblcf
[vcpkg]: https://github.com/Microsoft/vcpkg
