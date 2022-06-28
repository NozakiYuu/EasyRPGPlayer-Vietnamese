# EasyRPG Player

EasyRPG Player là một trình biên dịch trò chơi để chơi những trò chơi RPG Maker 2000, 2003 và các trò chơi EasyRPG. Nó sử dụng thư viện phân tích LCF (liblcf) để đọc dữ liệu trò chơi RPG Maker.

EasyRPGPlayer-Vietnamese là một bản chỉnh sửa của phần mềm này và nó được thêm khả năng hỗ trợ phông chữ tiếng Việt và làm cho trò chơi có thể sử dụng ngôn ngữ tiếng Việt.<br>
Bản chỉnh sửa này được lấy cảm hứng rất lớn từ [bản của toaranotdev](https://github.com/toaranotdev/easyrpg-player-vietnamese), nên bạn cũng có thể ghé qua bản của em ấy.

EasyRPG Player là một phần của dự án EasyRPG. Thông tin thêm bằng tiếng Anh có thể tìm thấy ở trang web của dự án: [https://easyrpg.org](https://easyrpg.org) 

## Làm thế nào để dịch môt trò chơi RPG2000/2003 sang tiếng Việt?

Dùng công cụ [lcftrans](https://ci.easyrpg.org/view/Tools/) (cũng từ dự án EasyRPG) để xuất các dòng chữ và đoạn hội thoại của trò chơi và bạn chỉ cần dịch nó là xong. Bản này hỗ trợ bảng mã Unicode nên bạn cũng có thể sử dụng Unicode nếu thích.

Và, trò chơi bạn cần dịch cần sử dụng Shinonome làm phông chữ để Player có thể hiển thị phông chữ tiếng Việt đã qua chỉnh sửa.

## Tài liệu hướng dẫn

Tài liệu hướng dẫn bằng tiếng Anh có thể được tìm thấy ở trang wiki của dự án: https://wiki.easyrpg.org


## Yêu cầu

### Quan trọng

- [liblcf] để đọc dữ liệu RPG Maker.
- SDL2 để hỗ trợ màn hình phụ.
- Pixman để quản lý hình ảnh pixel cấp thấp.
- libpng để hỗ trợ hình ảnh có định dạng PNG.
- zlib để hỗ trợ hình ảnh có định dạng XYZ.
- fmtlib để ghi nhật ký phần mềm.

### Khuyên dùng

- FreeType2 để hỗ trợ các phông chữ bên ngoài (+ HarfBuzz để hỗ trợ các phông chữ Unicode)
- mpg123 để hỗ trợ các tệp tin MP3 tốt hơn
- WildMIDI để hỗ trợ các tệp tin MIDI tốt hơn
- Libvorbis / Tremor để hỗ trợ các tệp tin OGG
- opusfile để hỗ trợ các tệp tin OPUS
- libsndfile để hỗ trợ các tệp tin WAV tốt hơn.
- libxmp để hỗ trợ âm nhạc theo dõi tốt hơn
- SpeexDSP để lấy lại mẫu âm thanh thích hợp

SDL 1.2 cũng được hỗ trợ nhưng không còn được sử dụng rộng rãi nữa.


## Các bản dựng thường xuyên

Các bản dựng tiếng Anh thường xuyên được xây dựng mỗi ngày bởi chính EasyRPG được tải lên ở trên website này.<br>
Các bản dựng này luôn dựa theo mã nguồn mới nhất trên GitHub chính thức của EasyRPG, nên một số lỗi vặt có thể xảy ra.

https://ci.easyrpg.org/view/Player/


## Source code

Mã nguồn gốc (bản tiếng Anh) của EasyRPG Player được tải lên GitHub và bạn có thể xem nó tại đây:

https://github.com/EasyRPG/Player

Các phiên bản đã được ra mắt cũng có sẵn ở trang web này:

https://easyrpg.org/downloads/player/


## Xây dựng từ mã nguồn

Bạn có thể xem [tài liệu dành cho xây dựng](https://github.com/NozakiYuu/EasyRPGPlayer-Vietnamese/blob/master/docs/BUILDING.md).


## Chạy EasyRPG Player

Chạy tệp tin `easyrpg-player` từ thư mục của trò chơi RPG Maker 2000/2003 mà bạn cần chơi (cùng thư mục với tệp tin `RPG_RT.exe`).

Nếu bạn chạy trên hệ điều hành Android, cần theo hướng dẫn có sẵn đã ghi ở trong phần mềm đó.


## Báo lỗi

Bạn có thể báo lỗi cho đội ngũ EasyRPG nếu như lỗi xuất phát từ Player gốc, còn nếu nó xuất phát từ Player bản tiếng Việt thì **hãy báo cáo cho nhà phát triển của bản tiếng Việt (Nozaki Yuu), không báo cáo cho bên EasyRPG**!

Nếu bạn báo lỗi với EasyRPG, vui lòng báo lỗi bằng tiếng Anh, không báo lỗi bằng tiếng Việt.

### Các tuỳ chọn có sẵn của đội ngũ EasyRPG:

* Báo lỗi tại trang web https://github.com/EasyRPG/Player/issues
* Mở một chủ đề tại diễn đàn https://community.easyrpg.org/
* Trò chuyện với đội ngũ EasyRPG: [#easyrpg at irc.libera.chat]

### Các tuỳ chọn có sẵn của Nozaki Yuu:

Trò chuyện qua Facebook: https://www.facebook.com/Yonaka12 hoặc qua Discord: Nozaki Yuu#0011.

## Giấy phép

EasyRPG Player là một phần mềm miễn phí có sẵn dưới giấy phép GPLv3. Đọc tệp tin [COPYING](/docs/COPYING.md) để xem điều kiện của giấy phép. Để xem thông tin tác giả hãy truy cập vào [tài liệu tác giả](https://github.com/NozakiYuu/EasyRPGPlayer-Vietnamese/blob/master/docs/AUTHORS.md).


### Phần mềm bên thứ ba (3rd party software)

EasyRPG Player sử dụng những phần mềm bên thứ ba sau:

* [FMMidi] YM2608 FM synthesizer emulator - Copyright (c) 2003-2006 yuno
  (Yoshio Uno), provided under the (3-clause) BSD license
* [dr_wav] WAV audio loader and writer - Copyright (c) David Reid, provided
  under public domain or MIT-0
* [PicoJSON] JSON parser/serializer - Copyright (c) 2009-2010 Cybozu Labs, Inc.
  Copyright (c) 2011-2015 Kazuho Oku, provided under the (2-clause) BSD license
* [Dirent] interface for Microsoft Visual Studio -
  Copyright (c) 2006-2012 Toni Ronkko, provided under the MIT license
* [rang] terminal color library - by Abhinav Gauniyal, provided under Unlicense

### Tài nguyên bên thứ ba (3rd party resources)

* [Baekmuk] font family (Korean) - Copyright (c) 1986-2002 Kim Jeong-Hwan,
  provided under the Baekmuk License
* [Shinonome] font familiy (Japanese) - Copyright (c) 1999-2000 Yasuyuki
  Furukawa and contributors, provided under public domain. Glyphs were added
  and modified for use in EasyRPG Player, all changes under public domain.
* [ttyp0] font family - Copyright (c) 2012-2015 Uwe Waldmann, provided under
  ttyp0 license
* A modded version of [gohufont](https://github.com/hchargois/gohufont) font family - Copyright (c) 2015 Hugo Chargois, WTFPL license
* [WenQuanYi] font family (CJK) - Copyright (c) 2004-2010 WenQuanYi Project
  Contributors provided under the GPLv2 or later with Font Exception
* [Teenyicons] Tiny minimal 1px icons - Copyright (c) 2020 Anja van Staden,
  provided under the MIT license (only used by the Emscripten web shell)

[liblcf]: https://github.com/EasyRPG/liblcf
[#easyrpg at irc.libera.chat]: https://kiwiirc.com/nextclient/#ircs://irc.libera.chat/#easyrpg?nick=rpgguest??
[FMMidi]: http://unhaut.epizy.com/fmmidi
[dr_wav]: https://github.com/mackron/dr_libs
[PicoJSON]: https://github.com/kazuho/picojson
[Dirent]: https://github.com/tronkko/dirent
[rang]: https://github.com/agauniyal/rang
[baekmuk]: https://kldp.net/baekmuk
[Shinonome]: http://openlab.ring.gr.jp/efont/shinonome
[ttyp0]: https://people.mpi-inf.mpg.de/~uwe/misc/uw-ttyp0
[WenQuanYi]: http://wenq.org
[Teenyicons]: https://github.com/teenyicons/teenyicons
