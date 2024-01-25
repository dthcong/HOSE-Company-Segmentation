# HOSE Company Segmentation
![image](https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/caee6380-3db7-454c-8c1d-43ee81f9bbde)

## Overview

Project thể hiện quá trình scraping data để lấy và tổng hợp thông tin chứng khoán (Tên Công ty, Mã chứng khoán, ngành Công Nghiệp, Giá trị cổ phiếu, ...) cùng các thông tin tài chính (Tổng doanh thu, Tổng lợi nhuận, Tổng tài sản, Tổng nợ, Tổng vốn lưu động ....) trong vòng 1 năm gần nhất của các Công ty niêm yết trên sàn HOSE (Sở Giao dịch Chứng khoán thành phố Hồ Chí Minh).

Từ đó tiến hành phân cụm các Công ty này bằng thuật toán Clustering dựa trên tốc độ tăng trưởng các chỉ số để tìm ra Nhóm công ty phát triển mạnh nhất, có niềm tăng đầu tư nhất.

Tham khảo [Project Dictionary](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/PROJECT%20DICTIONARY.xlsx)

## Dataset

Data sử dụng được tổng hợp từ các nguồn 24hmoney và Rồng Việt:
1. [B1_hse_comp](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/data/B1_hse_comp.csv): file csv chứa Danh sách Cty niêm yết sàn HOSE với tên Cty, mã CK, Ngành và khối lượng GD lấy từ [24hmoney](https://24hmoney.vn/companies).
2. [bctc](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/data/bctc.zip): folder chứa data raw được scrape từ website dữ liệu CK của Công ty Rồng Việt [data.vdsc](https://data.vdsc.com.vn/vi/Stock/VDS).
3. [B2_finance_record](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/data/B2_finance_record.csv): file csv chứa tỷ lệ tăng trưởng các chỉ số Chứng khoán & Tài chính quan trọng (Tổng doanh thu, Tổng lợi nhuận…) trong 1 năm gần nhất được xử lý - tổng hợp từ các file data raw trong folder bctc.

## Tool

- Google Colab, Pandas, Beautiful Soup: scrape và xử lý raw data lấy từ trang '24hmoney'.
- Selenium WebDriver: scrape data từ trang 'data.vdsc'.
- Scikit-Learn: tạo và triển khai các mô hình Clustering (K-Mean, DBSCAN ...).
- Seaborn: trực quan hóa.

## Code
1. [A1_Scraping_P1](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/code/A1_Scraping_P1.ipynb): chứa code để scraping data lần 1 là Danh sách Cty niêm yết HOSE từ trang '24hmoney'. Kết quả là file csv 'B1_hse_comp' dùng làm input của file A2 phía dưới.
2. [A2_Scraping_P2](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/code/A2_Scraping_P2.ipynb): chứa code scraping data chứng khoán - tài chính trong 1 năm gần nhất cho tất cả các Cty trong Ds nói trên từ trang 'data.vdsc'. Kết quả scrape được là các file data raw trong folder 'bctc'. Sau đó tiến hành xử lý và tổng hợp các file này vào 1 file csv là 'B2_finance_record'.
3. [AAA_Final_Project](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/code/AAA_Final_Project.ipynb): chứa code chạy thuật toán Clustering với input là file B2 nói trên và trình bày kết quả phân cụm các công ty.

## Sample Visualization

1. Số lượng các Công ty trong 4 Cụm:
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/4daeb3f6-7a1c-4a8f-9c9a-92a57c1b7068" width="33%"/>

2. Phân bổ các điểm dữ trong không gian 3D với chỉ số Tổng vốn (TV):
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/694cc8ce-0544-442e-83da-443a5e9bd557" width="50%"/>

3. Phân bổ các điểm dữ trong không gian 3D với chỉ số Giá trị sổ sách(BVPS):
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/1fc485bd-99f9-43a6-9cea-2beed372a18e" width="50%"/>

4. Tốc độ tăng trưởng Lợi Nhuận & Tổng Nợ trong 3 Quý gần nhất của 4 Cụm:
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/ff637b5b-d2a4-4019-a4f8-e71b8bb04ef5" width="33%"/>
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/cff2b203-6d1f-486c-9d39-134e15e4ac44" width="33%"/>

5. Biên độ gia tăng thị giá của 100 cổ phiếu tăng mạnh nhất HOSE sau 3 tháng kể từ T9/2023:
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/9b7d246a-d6b0-4a91-8dae-51c630d3338b" width="66%"/>

6. Biểu đồ Treemap thể hiện mức tăng thị giá của 100 CP nói trên:
<img src="https://github.com/dthcong/HOSE-Company-Segmentation/assets/156085700/94df660e-8ae4-460f-aca9-129eb81fbadc" width="66%"/>

## Result
[Insight](https://github.com/dthcong/HOSE-Company-Segmentation/blob/main/Project%20Insight.pdf)
