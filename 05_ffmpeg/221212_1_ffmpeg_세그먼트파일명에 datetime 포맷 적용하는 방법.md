# FFmpeg saving stream in intervals with date time as filename (FFmpeg에서 주기적으로 스트림을 저장할때, datetime 파일명을 적용하는 방법)

This is how to save a video stream in 60 second intervals with the current date and time as the filename using FFmpeg.

(해당 글은 FFmpeg에서 60초 간격으로 비디오 스트림을 저장할 때, 파일명으로 어떻게 날짜 및 시간을 활용한 포매팅을 적용할 수 있는지에 대한 내용을 다룹니다.)

Putting the saved stream into segments means you can access the saved content without having to stop the FFmpeg process.

(저장된 스트림을 세그먼트에 집어넣는다는 뜻은, FFmpeg 프로세스를 멈추지 않더라도 언제든지 저장된 컨텐츠에 접근할 수 있다는 뜻입니다.)

```cmd
ffmpeg -i inputurl -c copy -f segment -strftime 1
-segment_time 60 %Y-%m-%d-%H-%M-%S.mp4
```

`-segment_time 60` makes each ‘video’ (segment) 60 seconds long.

(`-segment_time 50`은 비디오(세그먼트)를 60초 간격으로 만들겠다는 뜻입니다.)

`-strftime 1` allows for datetime formatting to be used in the output name.

(`-strftime 1`은 output을 이름으로 datetime 포매팅을 허용한다는 뜻입니다.)

%Y is year, %m month, %d day of the month, %H is hour in 24h format, %M is minute and %S is seconds.

(%Y는 년도, %m은 월, %d는 해당월의 일, %H는 24시간 기준 시, %M는 분 그리고 %S는 초를 의미합니다.)

By using the above command i could see a filename sequence such as:

(위의 명령어를 사용하게되면, 아래와 같은 파일명 형태의 시퀀스를 확인할 수 있습니다.)

`2020-04-05-22-14-51.mp4`

`2020-04-05-22-15-51.mp4`

`2020-04-05-22-16-51.mp4`
