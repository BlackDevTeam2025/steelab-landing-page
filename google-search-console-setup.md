# Hướng dẫn cài đặt Google Search Console cho SteeLab.tech

## Bước 1: Đăng ký Google Search Console

1. Truy cập https://search.google.com/search-console/
2. Đăng nhập bằng tài khoản Google
3. Nhấn **"Add property"** (Thêm thuộc tính)
4. Chọn **"URL prefix"** và nhập: `https://steelab.tech`

## Bước 2: Xác thực quyền sở hữu website

### Phương pháp 1: HTML File Upload (Khuyến nghị)
1. Tải file HTML verification từ Google Search Console
2. Upload file này vào thư mục gốc của website: `/Users/blackpham/Desktop/project_khanh/`
3. Đảm bảo file có thể truy cập tại: `https://steelab.tech/[tên-file-verification].html`
4. Nhấn **"Verify"** trong Google Search Console

### Phương pháp 2: HTML Tag
1. Copy thẻ meta verification từ Google Search Console
2. Thêm vào phần `<head>` của file `index.html`:
```html
<meta name="google-site-verification" content="[verification-code]" />
```

## Bước 3: Submit Sitemap

1. Trong Google Search Console, vào mục **"Sitemaps"**
2. Nhập URL sitemap: `https://steelab.tech/sitemap.xml`
3. Nhấn **"Submit"**

## Bước 4: Cấu hình cơ bản

### 4.1 Set preferred domain
- Trong **"Settings"** > **"Address Change"**
- Đảm bảo chọn `https://steelab.tech` (có SSL)

### 4.2 Thiết lập crawl rate
- Vào **"Settings"** > **"Crawl rate"**
- Để mặc định hoặc tăng lên nếu server mạnh

### 4.3 Target country
- Vào **"Settings"** > **"International Targeting"**
- Chọn **Vietnam** làm target country

## Bước 5: Tối ưu cho Blockchain Keywords

### 5.1 Monitor Search Performance
- Theo dõi các từ khóa:
  - blockchain outsourcing vietnam
  - web3 development vietnam
  - smart contract development
  - defi development service
  - nft marketplace development

### 5.2 Submit URL manually
Khi có trang mới, submit trực tiếp:
- Sử dụng **"URL Inspection"** tool
- Nhập URL cần index
- Nhấn **"Request Indexing"**

## Bước 6: Monitor và tối ưu

### Performance Metrics cần theo dõi:
- **Impressions**: Số lần hiển thị trên Google
- **Clicks**: Số lần click vào website
- **CTR**: Click-through rate (tỷ lệ click)
- **Average Position**: Vị trí trung bình trên SERP

### Core Web Vitals:
- **LCP** (Largest Contentful Paint): < 2.5s
- **FID** (First Input Delay): < 100ms
- **CLS** (Cumulative Layout Shift): < 0.1

## Bước 7: Hành động cần thực hiện hàng tuần

1. **Kiểm tra Coverage Report**: Đảm bảo không có lỗi crawl
2. **Monitor Mobile Usability**: Website phải mobile-friendly
3. **Check Security Issues**: Đảm bảo không có malware
4. **Review Search Queries**: Tối ưu content cho các query mới

## Tips quan trọng:

### ✅ Nên làm:
- Submit sitemap thường xuyên khi có content mới
- Theo dõi error reports và fix ngay lập tức
- Tối ưu page speed (aim for < 3 seconds)
- Đảm bảo website responsive trên mobile
- Viết meta descriptions hấp dẫn cho từng trang

### ❌ Không nên:
- Submit quá nhiều URL cùng lúc
- Thay đổi cấu trúc URL thường xuyên
- Ignore mobile usability issues
- Quên update sitemap khi có trang mới

## Files cần có trong project:

✅ **sitemap.xml** - Đã tạo
✅ **robots.txt** - Đã tạo
✅ **Meta tags đầy đủ** - Đã có trong index.html
🔄 **SSL certificate** - Cần đảm bảo HTTPS
🔄 **Google verification file** - Sẽ có sau khi setup

**Lưu ý**: Việc indexing có thể mất 1-4 tuần, nhưng với proper setup này, website sẽ xuất hiện trên Google nhanh hơn và ranking tốt hơn!