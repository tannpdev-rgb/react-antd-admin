## Giới thiệu thư mục api

> Thư mục `api` dùng để lưu trữ toàn bộ các file gọi API. Cấu trúc được chia theo từng trang, mỗi trang tương ứng với một thư mục.
> Các thư mục có thể lồng nhau, nhưng trong mỗi thư mục bắt buộc phải có:
>
> * File chứa các hàm gọi API
> * File định nghĩa kiểu dữ liệu (type)

Dưới đây là một cấu trúc thư mục tiêu biểu: `src/api/user`:

```zsh
├── api
│   └── user                  # Trang người dùng, API được chia theo từng trang
│       ├── index.ts          # File định nghĩa các API request
│       └── types.ts          # File định nghĩa kiểu dữ liệu
```

Nếu trong một trang còn có các trang con, bạn có thể tiếp tục lồng thêm thư mục, ví dụ: `src/api/system`.

---

## Mô tả các file

### File định nghĩa kiểu dữ liệu (types)

Tên của các interface/type thường bắt đầu bằng tên trang tương ứng và kết thúc bằng hậu tố `Type`, ví dụ:

```ts
export interface RoleItemType {
	id: number
	createTime: number
	updateTime: number
	name: string
	code: string
	status: 1 | 0
	remark: string
}
```

---

### File định nghĩa request API

Một file request API tiêu chuẩn có dạng như sau:

> Các request tận dụng đầy đủ các HTTP method như `request.get`, `request.post`, …
> Việc bỏ qua animation loading được thực hiện thông qua tham số `ignoreLoading`.

Lưu ý quan trọng:

1. Với request **GET**, tham số truyền vào phải đặt trong object `searchParams`.
   Với các request **POST**, **PUT**, … tham số phải đặt trong object `json`.
2. Đường dẫn API **không được bắt đầu bằng dấu `/`**.

```ts
import type { RoleItemType } from "./types";
import { request } from "#src/utils/request";

export * from "./types";

/* Lấy danh sách role */
export function fetchRoleList(data: any) {
	return request.get<ApiListResponse<RoleItemType>>(
		"role-list",
		{ searchParams: data, ignoreLoading: true }
	).json();
}

/* Thêm role mới */
export function fetchAddRoleItem(data: RoleItemType) {
	return request.post<ApiResponse<string>>(
		"role-item",
		{ json: data, ignoreLoading: true }
	).json();
}

/* Cập nhật role */
export function fetchUpdateRoleItem(data: RoleItemType) {
	return request.put<ApiResponse<string>>(
		"role-item",
		{ json: data, ignoreLoading: true }
	).json();
}

/* Xóa role */
export function fetchDeleteRoleItem(id: number) {
	return request.delete<ApiResponse<string>>(
		"role-item",
		{ json: id, ignoreLoading: true }
	).json();
}
```

---

## Giới thiệu `request.ts`

`request.ts` là file dùng để **wrapper (đóng gói)** thư viện gọi HTTP **Ky**.
Chi tiết cách triển khai có thể xem tại: `src/utils/request`.

File này giúp:

* Chuẩn hóa cách gọi API trong toàn bộ project
* Quản lý loading, error, header, token… tập trung tại một nơi
* Giảm code lặp lại khi viết các hàm request
