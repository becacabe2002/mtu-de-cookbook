# Data Orchestration

* Cùng với sự phát triển của thế giới, lượng dữ liệu cá nhân người dùng được sinh ra hàng ngày tăng nhanh (175 ZB).

* Với lượng dữ liệu khổng lồ đó, việc xảy ra lỗi trong quá trình thu thập là không thể tránh khỏi
-> _**Cần sử dụng data orchestration**_.

## Định nghĩa
* Data Orchestration - quá trình thu thập dữ liệu (lớn) từ nhiều nguồn lưu trữ, với mục đích kết hợp và tổ chức nó.

* Mục đích chính là cho phép các công cụ phân tích dữ liệu có thể: lọc, sắp xếp, tổ chức và phát hành các dữ liệu phức tạp trong data-storing cloud.

* Các hành động như: monitoring, composing và lining up các data pipelines sử dụng dữ liệu từ các nguồn khác nhau.

## Lợi ích của Data Orchestration

* Tăng độ hiệu quả của các công cụ phân tích dữ liệu
    * Thu thập và tích hợp dữ liệu từ nhiều nguồn vào thành 1 pool duy nhất.
    -> Các công cụ phân tích dữ liệu có thể dễ dàng truy cập và phân tích dữ liệu mọi lúc.

* Giảm chi phí:
    * Giảm thiểu các lỗi của con người -> giảm chi phí đền bù
    * Tự động hóa các tác vụ -> giảm thiểu chi phí thuê nhân lực

* Loại bỏ tắc nghẽn dữ liệu:
    * Nguyên nhân thường đến từ việc xử lý sai dữ liệu, hoặc thiếu khả năng xử lý dữ liệu (đặc biệt trong các trường hợp có lưu lượng lớn)
    * Data Orchestration cho phép tự động hóa việc sắp xếp, xử lý dữ liệu cùng lúc với tổ chức dữ liệu
    -> Cần ít thời gian hơn cho việc thu thập và chuẩn bị dữ liệu -> Giảm/loại bỏ tắc nghẽn.

* Đảm bảo sự quản trị dữ liệu:
    * Tuân thủ các tiêu chuẩn, chính sách khi quản lý dữ liệu là một điều quan trọng đối vói doanh nghiệp.
    * Data Orchestration tools cho phép kiểm tra, giám sát quá trình xử lý dữ liệu đến từ nhiều nguồn khác nhau, từ đó tuân thủ chiến lược xử lý dữ liệu của doanh nghiệp.

## Các Data Orchestration Tools/Platforms
* **[Rivery Data Orchestration](https://rivery.io/product/data-orchestration/)**:
    * No-Code Solution
    * Centralized DataOps
    * Automated Flow
    * Compatiable Data Transformation with Top Cloud DWHs

* **[Metaflow](https://metaflow.org/)**:
    * Implementation of DAGs
    * Python-based tool
    * Incorporates several data orchestration projects

* **[Stich](https://www.stitchdata.com/platform/orchestration/)**:
    * No-Code
    * Data management during flow
    * Error-handling features

* **[Apache Airflow](https://airflow.apache.org/)**:
    * Open-source
    * Free to use
    * Able to integrate with Google Cloud Platform (Cloud Composer), AWS, Azure
