# TCP Log Server

이 프로젝트는 차선 검출과 YOLO 객체 검출을 결합한 자동차 안전 시스템에서 얻은 정보를 전달받고, 로그에 저장하는 TCP 서버입니다.

## 기능

- **텍스트 로그 서버**: 포트 8080에서 텍스트 데이터를 받아 로그 파일에 저장
- **비디오 로그 서버**: 포트 8081에서 비디오 파일을 받아 저장
- **로그 관리**: 날짜별로 구분된 로그 파일 생성 및 관리
- **멀티스레딩**: 텍스트와 비디오 서버를 동시에 실행

## 빌드 및 실행

### 빌드 방법
```bash
mkdir build
cd build
cmake ..
make
```

### 실행 방법
```bash
./MyServerApp
```

## 파일 구조

```
showWarMessage-main/
├── CMakeLists.txt          # CMake 빌드 설정 파일
├── main.cpp                # 프로그램 시작점 (메인 함수)
├── server.cpp              # TCP 서버 구현 (텍스트/비디오 로그 서버)
├── server.h                # 서버 함수 선언 헤더
├── save_log.cpp            # 로그 저장 유틸리티 함수
├── save_log.h              # 로그 저장 함수 선언 헤더
├── logs/                   # 로그 파일 저장 폴더
│   └── logs_YYYY-MM-DD.ini # 날짜별 로그 파일
├── build/                  # 빌드 결과물 (gitignore됨)
├── .vscode/                # VS Code 설정
│   ├── settings.json
│   └── tasks.json
└── README.md               # 프로젝트 설명서
```

## 서버 포트

- **텍스트 로그 서버**: 포트 8080
- **비디오 로그 서버**: 포트 8081

## 로그 파일 형식

텍스트 로그는 INI 형식으로 저장되며, 날짜별로 파일이 생성됩니다:
```
[ClientLog]
2024-01-01 12:00:00 = 받은 데이터 내용
2024-01-01 12:00:01 = 다른 데이터 내용
```

비디오 파일은 `received_videos/` 폴더에 타임스탬프와 함께 저장됩니다.

## 개발 환경

- **언어**: C++17
- **빌드 시스템**: CMake 3.10+
- **플랫폼**: Linux/Unix (POSIX 소켓 사용)


