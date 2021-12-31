# WASM GOLANG

Đây là một ví dụ cụ thể về ngôn ngữ lập trình.

### Install
1. Download using the [GitHub .zip](https://github.com/dracula/atom.git) download option and unzip them
2. Move the dracula-syntax folder to ~/.atom/packages

### Activate
Go to Atom -> Preferences..., click in the Themes tab, and select Dracula in the Syntax Theme dropdown.

### Modified
- Cần sửa 01 hàm f8e4d138ef5c47ea2c7b3e5c để đọc dữ liệu từ Indexeddb vào bộ nhớ
- Cần sửa 03 hàm f4da5d4d01f8e40a3e6f5c136 để load dữ liệu từ binary vào indexeddb
- Cần sửa lại một số hàm về tạo các đối tượng DOM
- Cần sửa về hàm gọi cookie để lấy dữ liệu chính xác
- Cần sửa hàm gọi ajax hoặc các hàm khác về mà sử dụng jquery về pure javascript

### Mang P2P
- [xay dung p2p voi rust](https://github.com/zupzup/rust-peer-to-peer-example)

### Rust large read

You can use BufReader's read_until function. It is very similar to File's read_to_end, but also takes a byte delimiter argument. This delimiter can be any byte, and a newline \n byte would be suitable for you. Afterwards, you can just lossily convert the buffer from UTF-8. It would look something like this:

```rust
let file = File::open("foo.txt")?;
let mut reader = BufReader::new(file);
let mut buf = vec![];

while let Ok(_) = reader.read_until(b'\n', &mut buf) {
    if buf.is_empty() {
        break;
    }
    let line = String::from_utf8_lossy(&buf);
    println!("{}", line);
    buf.clear();
}

Ok(())
```

Of course, this could be abstracted away into an iterator, just like Lines is done, but the basic logic is the same as above.

NOTE: unlike the lines function, the resulting strings will include the newline character, and the carriage return (\r) if there is one. It will be needed to strip those characters away, if the behaviour of the solution has to match the lines function.
