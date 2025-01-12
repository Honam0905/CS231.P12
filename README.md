<p align="center">
  <a href="https://www.uit.edu.vn/" title="Trường Đại học Công nghệ Thông tin" style="border: 5;">
    <img src="https://i.imgur.com/WmMnSRt.png" alt="Trường Đại học Công nghệ Thông tin | University of Information Technology">
  </a>
</p>

<!-- Title -->
<h1 align="center"><b>CS231.P12 - Nhập môn thị giác máy tính</b></h1>


## GIỚI THIỆU

<a name="gioithieumonhoc"></a>

- **Tên môn học**: Nhập môn thị giác máy tính
- **Đề tài**: Zero-Shot Object Counting
- **Mã môn học**: CS231.P12
- **Năm học**: 2024-2025

## GIẢNG VIÊN HƯỚNG DẪN

<a name="giangvien"></a>

- TS **Mai Tiến Dũng**

## THÀNH VIÊN NHÓM

<a name="thanhvien"></a>
| STT | MSSV | Họ và Tên | Github | Email |
| ------ |:-------------:| ----------------------:|-----------------------------------------------------:|-------------------------:
| 1 | 22520915 | Nguyễn Hồ Nam |[Honam0905 ](https://github.com/Honam0905) |22520915@gm.uit.edu.vn |

## Lưu ý khi chạy code
- Vì thư mục gốc có sử dụng một số thư viện cũ không phù hợp và đường dẫn bị sai vì dùng dataset ở địa chỉ khác nên cần phải chỉnh sửa trước khi chạy câu lệnh cuối cùng trong file CLIP-Count.ipynb
- Đầu tiên sau khi clone github gốc về truy cập vào thư mục util sau đó vào file misc.py ở dòng 23 thay thế torch._six bằng torch thông thường
- Ở file FSC147.py cần sửa lại một vài chỗ:
   + Đầu tiên ở dòng 45 thay thế self.data_dir bằng đường dẫn phù hợp được định nghĩa trong Load Dataset của file CLIP-Count.ipynb sau đó thay thế  self.dataset_type = 'FSC_147' ở dòng tiếp theo
bằng self.dataset_type = 'FSC147' 
   + Tiếp theo ở dòng 49,50 cần thêm self.dataset_type sau self.data_dir để đảm bảo đường dẫn đúng
   + Ở dòng 52 thay thế Train_Test_Val_{self.dataset_type}.json bằng Train_Test_Val_FSC_147.json trong dấu ' ' tránh bị sai đường dẫn
   + Ở dòng thứ 83 cần thay thế đường dẫn phù hợp cho util/CLIP_caption.pkl
- Ở file run.py dòng thứ 566 và 567 gradio không sử dụng input nên chỉ cần bỏ đi input sửa lại thành gr.Image và gr.Textbox
- Ở file run.py dòng thứ 570 bỏ đi câu lệnh interpretation="default" do câu lệnh này không tương thích với phiên bản gradio
- Sau khi sửa các lỗi trên chạy lại dòng lệnh Code Running bình thường và chú ý rằng phải download file clipcount_pretrained.ckpt nằm trong thư mục gốc về 
```bash
!CUDA_VISIBLE_DEVICES=0 python /content/CLIP-Count/run.py --mode app --exp_name exp --batch_size 32 --ckpt /content/drive/MyDrive/Colab\ Notebooks/clipcount_pretrained.ckpt
```
