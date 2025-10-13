# React Native Menu App

## 프로젝트 개요
VSCode를 활용하여 개발하는 React Native + Expo 기반의 크로스플랫폼 앱으로, Material Design을 적용한 메뉴 기반 예제 애플리케이션입니다. Android, iOS, 웹 환경에서 모두 실행 가능합니다.

## 요구사항

### 기본 요구사항
- **플랫폼**: Android, iOS, Web 크로스플랫폼
- **개발 도구**: VSCode
- **언어**: TypeScript (React Native)
- **프레임워크**: Expo
- **디버깅**: 웹을 통한 디버깅 지원
- **유연성**: 확장 가능한 아키텍처

### 기능 요구사항
1. **메인 화면**
   - 앱 제목 표시
   - 간단한 앱 소개

2. **메뉴 구성**
   - 홈 (Home)
   - 프로필 (Profile)  
   - 설정 (Settings)
   - 정보 (About)

3. **네비게이션**
   - 하단 탭 네비게이션 구현
   - 화면 간 전환

4. **UI/UX**
   - Material Design 컴포넌트 사용
   - 반응형 디자인
   - 직관적인 사용자 인터페이스

### 기술 요구사항
- **프레임워크**: React Native + Expo
- **언어**: TypeScript
- **네비게이션**: React Navigation
- **UI 컴포넌트**: React Native Paper
- **개발 환경**: VSCode
- **디버깅**: 웹 디버깅 지원 (Expo DevTools)
- **번들러**: Metro Bundler

## 예상 파일 구조
```
MenuApp/
├── App.tsx                 # 메인 앱 컴포넌트
├── package.json            # 프로젝트 설정
├── index.ts                # 진입점 파일
├── screens/
│   ├── HomeScreen.tsx      # 홈 화면
│   ├── ProfileScreen.tsx   # 프로필 화면
│   ├── SettingsScreen.tsx  # 설정 화면
│   └── AboutScreen.tsx     # 정보 화면
├── navigation/
│   └── BottomTabNav.tsx    # 하단 탭 네비게이션
└── assets/
    ├── adaptive-icon.png   # 적응형 아이콘
    ├── favicon.png         # 파비콘
    ├── icon.png           # 앱 아이콘
    └── splash-icon.png    # 스플래시 아이콘
```

## 개발 단계
1. 개발 환경 설정 (Node.js, npm, Expo CLI)
2. VSCode 확장 프로그램 설치
3. Expo 프로젝트 생성
4. 웹 디버깅 환경 구성
5. 기본 앱 구조 설정
6. 샘플 앱 개발 및 테스트

## 설치 및 실행 방법
```bash
# 프로젝트 설치
npm install

# Expo 개발 서버 시작 (모든 플랫폼)
npx expo start

# Android 에뮬레이터에서 실행
npx expo start --android

# iOS 시뮬레이터에서 실행
npx expo start --ios

# 웹 브라우저에서 실행
npx expo start --web

# 오프라인 모드로 실행 (네트워크 문제 시)
EXPO_OFFLINE=true npx expo start
```

## 개발 환경
- **IDE**: VSCode
- **Node.js**: 최신 LTS 버전
- **Expo CLI**: 최신 버전
- **Android Studio**: Android 개발을 위한 에뮬레이터 (선택 사항)
- **Expo Go**: 모바일 디버깅을 위한 앱 (선택 사항)
