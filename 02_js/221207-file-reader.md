# input 태그로 선택한 이미지 파일 띄우기

## 내용 정리

- FileReader는 비동기적으로 File or Blob 객체를 읽어들이거나, 저장하는 용도로 사용된다.

- FileReader.onload() 이벤트는 리소스 객체를 읽어들이는게 성공했을 때 발생한다. 로드된 리소스 객체의 위치 경로는 콜백으로 전달받은 이벤트 객체의 e.target.result를 통해서 알 수 있다.

- FileReader.readAsDataURL()를 통해서 File 또는 Blob 객체에 있는 리소스를 읽어들인다.

## 샘플 소스코드

```js
$('#file1').on('change', function () {
  readFile(this)
})

function readFile(input) {
  if (input.files && input.files[0]) {
    var previewName = '#' + input.id + '_preview'

    var reader = new FileReader()
    reader.onload = function (e) {
      $(previewName).attr('src', e.target.result)
    }
    reader.readAsDataURL(input.files[0])
  }
}
```
