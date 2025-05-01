# ArgoCD ApplicationSet Helm 템플릿

이 저장소는 ArgoCD ApplicationSet과 Helm 차트를 사용하여 로컬 쿠버네티스 클러스터(Minikube 또는 Kind와 같은)에 여러 애플리케이션을 배포하기 위한 템플릿을 포함하고 있습니다.

## 저장소 구조

```
.
├── .gitignore
├── README.md
├── argocd
│   ├── applicationset.yaml
│   └── bootstrap.yaml
├── charts
│   ├── app1
│   │   ├── Chart.yaml
│   │   └── values.yaml
│   ├── app2
│   │   ├── Chart.yaml
│   │   └── values.yaml
│   └── base
│       ├── Chart.yaml
│       ├── templates
│       │   ├── deployment.yaml
│       │   └── service.yaml
│       └── values.yaml
└── environments
    ├── dev
    │   └── values.yaml
    └── prod
        └── values.yaml
```

## 사용 방법

1. **ArgoCD 설치:** 공식 ArgoCD 문서를 참고하여 클러스터에 설치합니다.
2. **ApplicationSet 부트스트랩:** 다음 명령어로 ApplicationSet 컨트롤러를 배포하기 위한 부트스트랩 애플리케이션을 적용합니다:
    ```bash
    kubectl apply -f argocd/bootstrap.yaml -n argocd
    ```
3. **커스터마이징:** 필요에 따라 Helm 차트와 환경 값을 수정합니다.
4. **커밋 및 푸시:** 변경사항을 Git 저장소에 커밋합니다.
5. **동기화:** ArgoCD가 자동으로 ApplicationSet을 감지하고 각 환경에 정의된 애플리케이션을 배포합니다. 