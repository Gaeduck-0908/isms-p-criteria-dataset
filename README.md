# isms-p-criteria-dataset

ISMS-P(정보보호 및 개인정보보호 관리체계) 인증기준 안내서(2023.11.23)를 구조화한 JSON 데이터셋입니다.

## 개요

KISA에서 발간한 ISMS-P 인증기준 안내서 PDF를 파싱하여, 101개 인증기준 항목을 검색·활용 가능한 JSON 형태로 정리했습니다.

## 데이터 구조

```json
{
  "title": "ISMS-P 인증기준 안내서",
  "version": "2023.11.23",
  "total_criteria": 101,
  "areas": [ ... ],
  "criteria": [ ... ]
}
```

### 인증기준 항목 필드

| 필드 | 설명 | 비고 |
|------|------|------|
| `code` | 항목 번호 (예: `1.1.1`) | 필수 |
| `title` | 항목명 | 필수 |
| `area` | 영역명 | 필수 |
| `domain` | 분야명 | 필수 |
| `description` | 인증기준 설명 | 101개 |
| `key_checks` | 주요 확인사항 | 101개 |
| `related_laws` | 관련 법규 | 75개 |
| `defect_cases` | 결함 사례 | 101개 |
| `full_content` | 원문 전체 텍스트 | 101개 |

### 영역 구성

| 영역 | 항목 수 |
|------|---------|
| 1. 관리체계 수립 및 운영 | 16개 |
| 2. 보호대책 요구사항 | 64개 |
| 3. 개인정보 처리 단계별 요구사항 | 21개 |

## 활용 예시

```python
import json

with open("data.json", encoding="utf-8") as f:
    data = json.load(f)

# 키워드 검색
keyword = "암호화"
results = [c for c in data["criteria"] if keyword in c.get("full_content", "")]
for r in results:
    print(f"{r['code']} {r['title']}")
```

## 출처

- [ISMS-P 인증기준 안내서 (2023.11.23)](https://isms-p.kisa.or.kr) — 한국인터넷진흥원(KISA)
