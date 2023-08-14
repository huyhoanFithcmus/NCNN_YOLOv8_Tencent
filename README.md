# NCNN_YOLOv8_Tencent
# Cách huấn luyện model học về biển báo giao thông sử dụng Yolo v8

Ở tài liệu này, chúng sẽ học về cách sử dụng yoloV8 cho việc huấn luyện 1 model học về nhận diện biển báo giao thông

## Cài đặt Git
- Windows: [link](https://git-scm.com/download/win)
- MacOs: [link](https://git-scm.com/download/mac)

## Cài đặt yolo

- Sử dụng [pip](https://pip.pypa.io/en/stable/) để cài đặt yolo.
- Vào thư mục nào mà các bạn muốn lưu trữ yolo, mở terminal ở thư mục đó, chạy từng câu lệnh sau

```bash
mkdir yolov8
cd yolov8
git clone https://github.com/ultralytics/ultralytics
pip install -qe ultralytics
cd ultralytics
```

## Cách sử dụng
- Dùng yolov8 để test ảnh xxx.png, ta dùng như sau
```bash
# image
$ yolo task=detect mode=predict model=yolov8m.pt source="XXX.png"
```
- Dùng yolov8 để test video xxx.mp4, ta dùng như sau, 
```
# video
$ yolo task=detect mode=predict model=yolov8m.pt source="XXX.mp4"
```
### Lưu ý, video và ảnh phải đúng đường dẫn ở source, cách tốt nhất là để video hoặc ảnh cần kiểm tra trong thư mục ultralytics

## Tải data về máy tính
#### Nhấn vào [link](https://drive.google.com/drive/folders/1vyaOBtJ0_5l9bCX_JSiCTcyGeUq9loSG?usp=sharing) này để tải file nén datasets xuống máy tính của bạn, giải nén sau khi tải về và đưa vào thư mục yolov8

#### Vào lại link [Drive](https://drive.google.com/drive/folders/1vyaOBtJ0_5l9bCX_JSiCTcyGeUq9loSG?usp=sharing) này tải file chip.yaml và để vào trong thư mục ultralytics

- sau khi tải các dữ kiện cần thiết, cây thư mục của bạn sẽ như hình dưới:
![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*tyQNVleILClJ6QB3QQEjYQ.png)

## Huấn luyện
- Vào thư mục ultralytics, mở terminal trong thư mục đó, chạy câu lệnh sau

```bash
yolo task=detect mode=train model=yolov8x.pt data=./chip.yaml epochs=30 imgsz=416   
```
#### Trong đó
- task=detect: công việc của yolo là detect 
- mode=train: chế độ huấn luyện dữ liệu
- model=yolov8n.pt: sử dụng model yolov8n để huấn luyện, các bạn có thể đổi sang yolov8s để huấn luyện
- data=./chip.yaml: gọi data để huấn luyện
- imgsz: số image trong tập huấn luyện
- epochs: số vòng lặp huấn luyện, ở đây mình cho là 30 để việc học đạt kết quả ổn định nhất

#### Lưu ý
Sau khi huấn luyện xong sẽ có dòng như sau:
```bash
Speed: 0.0ms preprocess, 293.1ms inference, 0.0ms loss, 0.3ms postprocess per image
Results saved to runs\detect\trainX
```
Từ đó khi kiểm tra, phải vào đúng thư mục trainX
## Kiểm tra việc huấn luyện có đạt kết quả mong đợi hay không
- Tại thư mục ultralytics, các bạn lưu đại 1 hình ảnh về và để trong thư mục ultralytics

- vào terminal, chạy câu lệnh sau
```bash
yolo task=detect mode=predict model=./runs/detect/trainX/weights/best.pt conf=0.25 source='XXX.png'
```
#### Trong đó
- task=detect: công việc của yolo là detect
- mode=predict: chế độ dự đoán dữ liệu
- model=./runs/detect/trainX/weights/best.pt: là model các bạn đã huấn luyện xong
- conf=0.25: độ tin cậy bằng 25%, các bạn có thể đổi độ tin cậy lên 
- source='XXX.png': thay xxx.png bằng file ảnh lúc nãy các bạn đã lưu trong thư mục ultralytics

# Cách huấn luyện model học về biển báo giao thông sử dụng Yolo v8

Ở tài liệu này, chúng sẽ học về cách sử dụng yoloV8 cho việc huấn luyện 1 model học về nhận diện biển báo giao thông

## Cài đặt Git
- Windows: [link](https://git-scm.com/download/win)
- MacOs: [link](https://git-scm.com/download/mac)

## Cài đặt yolo

- Sử dụng [pip](https://pip.pypa.io/en/stable/) để cài đặt yolo.
- Vào thư mục nào mà các bạn muốn lưu trữ yolo, mở terminal ở thư mục đó, chạy từng câu lệnh sau

```bash
mkdir yolov8
cd yolov8
git clone https://github.com/ultralytics/ultralytics
pip install -qe ultralytics
cd ultralytics
```

## Cách sử dụng
- Dùng yolov8 để test ảnh xxx.png, ta dùng như sau
```bash
# image
$ yolo task=detect mode=predict model=yolov8m.pt source="XXX.png"
```
- Dùng yolov8 để test video xxx.mp4, ta dùng như sau, 
```
# video
$ yolo task=detect mode=predict model=yolov8m.pt source="XXX.mp4"
```
### Lưu ý, video và ảnh phải đúng đường dẫn ở source, cách tốt nhất là để video hoặc ảnh cần kiểm tra trong thư mục ultralytics

## Tải data về máy tính
#### Nhấn vào [link](https://drive.google.com/drive/folders/1vyaOBtJ0_5l9bCX_JSiCTcyGeUq9loSG?usp=sharing) này để tải file nén datasets xuống máy tính của bạn, giải nén sau khi tải về và đưa vào thư mục yolov8

#### Vào lại link [Drive](https://drive.google.com/drive/folders/1vyaOBtJ0_5l9bCX_JSiCTcyGeUq9loSG?usp=sharing) này tải file chip.yaml và để vào trong thư mục ultralytics

- sau khi tải các dữ kiện cần thiết, cây thư mục của bạn sẽ như hình dưới:
![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*tyQNVleILClJ6QB3QQEjYQ.png)

## Huấn luyện
- Vào thư mục ultralytics, mở terminal trong thư mục đó, chạy câu lệnh sau

```bash
yolo task=detect mode=train model=yolov8x.pt data=./chip.yaml epochs=30 imgsz=416   
```
#### Trong đó
- task=detect: công việc của yolo là detect 
- mode=train: chế độ huấn luyện dữ liệu
- model=yolov8n.pt: sử dụng model yolov8n để huấn luyện, các bạn có thể đổi sang yolov8s để huấn luyện
- data=./chip.yaml: gọi data để huấn luyện
- imgsz: số image trong tập huấn luyện
- epochs: số vòng lặp huấn luyện, ở đây mình cho là 30 để việc học đạt kết quả ổn định nhất

#### Lưu ý
Sau khi huấn luyện xong sẽ có dòng như sau:
```bash
Speed: 0.0ms preprocess, 293.1ms inference, 0.0ms loss, 0.3ms postprocess per image
Results saved to runs\detect\trainX
```
Từ đó khi kiểm tra, phải vào đúng thư mục trainX
## Kiểm tra việc huấn luyện có đạt kết quả mong đợi hay không
- Tại thư mục ultralytics, các bạn lưu đại 1 hình ảnh về và để trong thư mục ultralytics

- vào terminal, chạy câu lệnh sau
```bash
yolo task=detect mode=predict model=./runs/detect/trainX/weights/best.pt conf=0.25 source='XXX.png'
```
#### Trong đó
- task=detect: công việc của yolo là detect
- mode=predict: chế độ dự đoán dữ liệu
- model=./runs/detect/trainX/weights/best.pt: là model các bạn đã huấn luyện xong
- conf=0.25: độ tin cậy bằng 25%, các bạn có thể đổi độ tin cậy lên 
- source='XXX.png': thay xxx.png bằng file ảnh lúc nãy các bạn đã lưu trong thư mục ultralytics

#### sau khi huấn luyện, các bạn vào thư mục ```runs\detect\predict6``` để xem kết quả
