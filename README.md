# 🏭 생산 관리 대시보드

QR 코드 스캔 기반 실시간 생산 관리 시스템입니다.

## 📋 기능

### 👷 작업자 기능
- **설비 QR 코드 스캔**: 작업할 설비 선택
- **작업표준서 QR 코드 스캔**: 작업 내용 확인
- **작업 시작/완료**: 생산 수량 입력 후 완료 보고
- **작업자 정보 관리**: 작업자 이름 설정

### 📊 대시보드
- **실시간 생산 통계**: 총 생산량, 진행 중인 작업, 승인 대기, 완료된 작업
- **작업 현황 카드**: 각 작업의 상태와 세부 정보 표시
- **진행 상황 추적**: 설비별, 작업자별 생산 현황

### ✅ 승인 관리
- **승인 대기 작업 목록**: 완료 보고된 작업 확인
- **일괄 승인/반려**: 관리자가 작업 승인 및 반려
- **승인 기록 관리**: 승인 시간 및 관리자 정보 자동 기록

## 🚀 GitHub Pages 배포 방법

### 1. GitHub 저장소 생성
```bash
# GitHub에서 새 저장소 생성 (production-dashboard)
# 저장소 URL: https://github.com/[username]/production-dashboard
```

### 2. 로컬 저장소 설정
```bash
git clone https://github.com/[username]/production-dashboard.git
cd production-dashboard
```

### 3. 파일 추가
```bash
# 아래 파일들을 저장소 루트에 복사:
- production_dashboard.html
- README.md
```

### 4. 파일 이름 변경
```bash
# GitHub Pages에서 index.html로 요청하므로
mv production_dashboard.html index.html
```

### 5. 커밋 및 푸시
```bash
git add .
git commit -m "Add production dashboard"
git push origin main
```

### 6. GitHub Pages 활성화
GitHub 저장소 설정 → Pages → 
- Source: main branch
- Folder: / (root)
- Save

### 7. 접속
https://[username].github.io/production-dashboard/

## 💾 데이터 저장

로컬스토리지를 사용하므로:
- 같은 브라우저에서는 데이터가 유지됨
- 다른 기기에서 접속하면 초기화됨
- 공유하려면 클라우드 백업 필요

## 📱 사용 방법

### 작업자 (👷 탭)
1. 작업자 이름 입력
2. 설비 QR 코드 스캔 (또는 설비 ID 입력)
3. 작업표준서 QR 코드 스캔 (또는 작업표준서 ID 입력)
4. "작업 시작" 클릭
5. 작업 완료 후 생산 수량 입력
6. "작업 완료 보고" 클릭

### 관리자 (✅ 탭)
1. 승인 관리 탭 이동
2. 완료 보고된 작업 확인
3. 승인 또는 반려 선택
4. 대시보드에서 통계 확인

## 🛠️ 커스터마이징

### QR 코드 추가
```html
<!-- 설비 QR 코드 생성 (설비별) -->
<script>
QRCode.toDataURL('EQUIPMENT_CNC20', {
    width: 300,
    margin: 1
}, function(err, url) {
    if (err) throw err;
    console.log(url);
})
</script>
```

### 데이터 백업
브라우저 개발자도구 → Application → Local Storage → productionData

## 📊 데이터 구조

```javascript
// 작업 기록
{
    id: "timestamp",
    equipment: "CNC20",
    standard: "GL714O6000/C",
    quantity: 50,
    worker: "이영우",
    startTime: "14:30:45",
    status: "approved|pending|rejected",
    timestamp: 1234567890
}
```

## 🔗 관련 파일

- `production_dashboard.html` - 메인 애플리케이션
- `README.md` - 이 문서
- 개별 설비용 QR 코드 (별도 생성 가능)

## 💡 팁

- 설비 ID 형식: `CNC20`, `CNC30` 등으로 통일
- 작업표준서 ID 형식: `GL714O6000/C`, `AX_237` 등
- 브라우저 캐시 삭제하면 모든 데이터 초기화됨
- 정기적으로 데이터 백업 권장

## 📞 지원

문제가 발생하면:
1. 브라우저 콘솔(F12) 확인
2. 로컬스토리지 데이터 확인
3. 캐시 삭제 후 재로드

---

**작성일**: 2024.05.20
**버전**: 1.0.0
