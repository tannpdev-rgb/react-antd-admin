<div align="center">
	<a href="https://github.com/condorheroblog/react-antd-admin/">
		<img alt="React-antd-admin Logo" width="192" src="https://github.com/user-attachments/assets/1de76309-4cf5-4e34-a32f-92c361bace2a">
	</a>
	<br />
	<h1>React Antd Admin</h1>
	<br />
</div>

![GitHub license](https://img.shields.io/github/license/condorheroblog/react-antd-admin?style=flat)
![GitHub stars](https://img.shields.io/github/stars/condorheroblog/react-antd-admin?color=fa6470\&style=flat)
![GitHub forks](https://img.shields.io/github/forks/condorheroblog/react-antd-admin?style=flat)

**English** | [中文](./README.zh-CN.md) | [Vietnamese](./README.zh-VN.md)

## Giới thiệu

react-antd-admin là một giải pháp dành cho hệ thống quản trị (middle office và back office) được xây dựng dựa trên React Hooks, Vite và TypeScript.
Mục tiêu của dự án là giúp bạn nhanh chóng xây dựng các hệ thống quản trị cấp doanh nghiệp, không cần cấu hình phức tạp, có thể sử dụng ngay sau khi cài đặt.

## Tính năng

* Stack công nghệ hiện đại: React Hooks, TypeScript, Vite, Ant Design, React Router, Tailwind CSS
* Thư viện quản lý state đơn giản và trực quan: Zustand
* Hỗ trợ đa ngôn ngữ: I18n
* Gửi request API: Ky, @tanstack/react-query
* Chuẩn hóa và format code: ESLint Flat Config
* Cache component theo route: keepalive-for-react
* Mock API: vite-plugin-fake-server
* Phân quyền routing: hỗ trợ cả routing tĩnh phía frontend và routing động từ backend
* Cấu hình theme: tích hợp sẵn nhiều theme, hỗ trợ dark mode, đồng bộ hệ màu giữa Ant Design và Tailwind CSS

## Xem demo

[react-antd-admin](https://condorheroblog.github.io/react-antd-admin/)

## Tài liệu

[Tài liệu react-antd-admin](https://condorheroblog.github.io/react-antd-admin/docs/)

## Cách sử dụng

### GitHub Template

[Tạo repository mới từ template này](https://github.com/new?template_name=react-antd-admin&template_owner=condorheroblog)

### Clone project

Nếu bạn muốn sử dụng template mà không giữ lại lịch sử git, hãy chạy các lệnh sau:

```bash
npx degit condorheroblog/react-antd-admin react-antd-admin
# hoặc npx giget@latest gh:condorheroblog/react-antd-admin react-antd-admin
cd react-antd-admin
corepack enable
pnpm i # Nếu chưa cài pnpm, chạy: npm install -g pnpm
```

## Phát triển

### Cài đặt

```bash
corepack enable

pnpm install
```

### Chạy project

```bash
pnpm run dev
```

Mở trình duyệt và truy cập:
[http://localhost:3333](http://localhost:3333) để xem kết quả.

## Build

```bash
pnpm build
```

Mặc định, sản phẩm build sẽ nằm trong thư mục `build`.

## Preview bản build

```bash
pnpm preview
```

## Ghi nhận

Cảm ơn các dự án sau đã truyền cảm hứng cho dự án này:

* vue-vben-admin: truyền cảm hứng về thiết kế
* vue-pure-admin: truyền cảm hứng về logic nghiệp vụ

## Lịch sử Star

[![Star History Chart](https://api.star-history.com/svg?repos=condorheroblog/react-antd-admin\&type=Date)](https://star-history.com/#condorheroblog/react-antd-admin&Date)

## Tài trợ

Nếu dự án này giúp ích cho bạn, bạn có thể ủng hộ tác giả bằng cách mời một bữa ăn mang về.

![Sponsor](https://camo.githubusercontent.com/b61a54a08ff3a1392f191016d6c0d7537559bb4fa19ae1d27fadfd1de5796289/68747470733a2f2f636f6e646f726865726f626c6f672e6769746875622e696f2f72656163742d616e74642d61646d696e2f646f63732f73706f6e736f722e706e67)

## Giấy phép

Giấy phép MIT © 2023–Hiện tại – Condor Hero
* Rút gọn README cho **portfolio**
* Giải thích README này cho **người mới React / Ant Design** từng phần một
