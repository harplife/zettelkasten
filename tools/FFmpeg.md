# FFmpeg
- 영상/오디오 처리 코맨드라인 도구
- [공식 문서](https://ffmpeg.org/documentation.html)
- [비디오 자르는 방법](https://shotstack.io/learn/use-ffmpeg-to-trim-video/)
- [고퀄 Video-to-GIF 변환 방법](https://superuser.com/a/556031)

## 설치
- Window 경우 Chocolatey 설치해주고 `choco install ffmpeg`

## 비디오 자르기
```powershell
ffmpeg -i input.mp4 -ss 00:00:47.300 -to 00:00:49.900 -c:v libx264 -c:a aac output.mp4
```

## Video to GIF 변환
```powershell
ffmpeg -i input.mp4 -vf "fps=10,scale=960:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" -loop 0 output.gif
```

- `scale` : 출력 이미지 가로 길이

### Examples
![[cosmos_ref_01.gif]]
![[cosmos_ref_05.gif]]
![[cosmos_ref_06.gif]]
![[cosmos_ref_07.gif]]
![[cosmos_2_ref_02.gif]]
![[cosmos_2_ref_03.gif]]
![[cosmos_2_ref_02 1.gif]]