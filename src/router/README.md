# Routing (Định tuyến)

Dự án sử dụng **React Router** để quản lý routing.
Mặc dù đang dùng phiên bản mới nhất là **v7**, nhưng tác giả khuyến nghị nên đọc **tài liệu v6** tại:
[https://reactrouter.com/en/6.28.1/](https://reactrouter.com/en/6.28.1/)

(Lý do đơn giản: cả hai bộ tài liệu đều không thật sự dễ đọc.)

---

## Thư mục routing

```bash
├── router
│   ├── constants.ts                      # Danh sách route trắng (không cần đăng nhập)
│   ├── extra-info                        # Thông tin mở rộng cho route
│   │   ├── index.ts
│   │   ├── route-path.ts                 # Định nghĩa path route, dùng cho điều hướng
│   │   │                                # Gom về một chỗ để dễ chỉnh sửa
│   │   └── order.ts                      # Thứ tự hiển thị menu route
│   ├── guards.tsx                        # Route guard (bảo vệ route)
│   ├── router-global-hooks.ts            # Hook toàn cục cho routing
│   ├── routes
│   │   ├── core                          # Các route cốt lõi
│   │   ├── modules                       # Route động (dynamic route)
│   │   └── static                        # Route tĩnh
│   ├── types.ts                          # Định nghĩa type cho routing
│   └── utils.ts                          # Các hàm tiện ích cho routing
```

---

## Component routing

Chỉ liệt kê các component thường dùng trong dự án:

| Tên component | Chức năng        | Mô tả                                     |
| ------------- | ---------------- | ----------------------------------------- |
| `<Link>`      | Điều hướng       | Dùng để chuyển trang                      |
| `<Outlet />`  | Container render | Dùng để hiển thị route con (nested route) |

---

## Hooks

### useMatches

Trả về **tất cả các route** đang khớp với route hiện tại.

```ts
import { useMatches } from "react-router";
const matches = useMatches();
console.log(matches);
// Kết quả: [{ pathname: '/path', params: {}, data: {} }, ...]
```

Từ `useMatches()` dự án đã tự đóng gói thêm hook `useCurrentRoute`
→ giúp lấy thông tin **route hiện tại mới nhất** một cách thuận tiện hơn.

---

### useParams

Dùng để lấy **tham số của route động**.

```ts
import { useParams } from "react-router";
const { id: templateId } = useParams<{ id: string }>();
```

---

### useNavigate

Dùng để **chuyển route bằng code**.

```ts
import { useNavigate } from "react-router";
const navigate = useNavigate();
navigate("/path");
```

---

### useLocation

Trả về object `location` của route hiện tại.

```ts
import { useLocation } from "react-router";
const location = useLocation();
console.log(location);
// Kết quả: 
// { pathname: '/path', search: '?x=1&y=2', hash: '', state: null, key: 'default' }
```

---

### useSearchParams

Dùng để đọc **query parameters** trên URL.

```ts
import { useSearchParams } from "react-router";
const [searchParams] = useSearchParams();
console.log(searchParams.get("x")); // Giá trị của tham số x
```

> Khuyến nghị dùng **nuqs** thay cho `useSearchParams` khi làm nghiệp vụ.
> `nuqs` cho phép quản lý **query parameters** đơn giản như `useState`.

```ts
import { useQueryState } from "nuqs";
const [hello, setHello] = useQueryState("hello", { defaultValue: "" });
```

---

### useOutlet

Trả về **React element** được tạo ra từ route hiện tại.

```ts
import { useOutlet } from "react-router";
const outlet = useOutlet();
console.log(outlet); // Ví dụ: <div>...</div>
```

Cơ chế **cache route** trong dự án được xây dựng dựa trên API này.

---

## Route Guard và Route Hook

Route guard và route hook được định nghĩa trong thư mục `src/router/guard`.

* `auth-guard.tsx`
  Route guard dùng để **kiểm tra quyền truy cập**

* `common-gurard.ts`
  Không kiểm tra quyền, nhưng hỗ trợ các logic chặn chung như:

  * Hiển thị loading
  * Xử lý trước / sau khi chuyển route
