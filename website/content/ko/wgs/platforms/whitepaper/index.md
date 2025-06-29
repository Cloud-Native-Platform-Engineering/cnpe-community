---
title:  "CNCF 플랫폼 백서(White Paper)"
pdf: https://github.com/Cloud-Native-Platform-Engineering/cnpe-community/raw/main/platforms-whitepaper/v1/assets/platforms-def-v1.0.pdf
version_info: https://github.com/Cloud-Native-Platform-Engineering/cnpe-community/tree/main/platforms-whitepaper/README.md
description: "이 백서는 기업 리더, 엔터프라이즈 아키텍트, 플랫폼 팀 리더가 클라우드 컴퓨팅을 위한 내부 플랫폼을 옹호하고, 조사하고, 계획할 수 있도록 지원하고자 합니다. 플랫폼은 기업의 실제 가치 흐름에 큰 영향을 미치지만 간접적으로만 영향을 미치므로 플랫폼 팀의 장기적인 지속 가능성과 성공을 위해서는 경영진의 합의와 지원이 필수적입니다. 이 백서에서는 플랫폼의 가치가 무엇인지, 이를 측정하는 방법, 그리고 이를 극대화하는 플랫폼 팀을 구현하는 방법에 대해 논의함으로써 이러한 지원을 가능하게 할 것입니다."
---

## 소개

데브옵스가 추구하는 부서 간 협력에서 영감을 받은 플랫폼 엔지니어링(Platform Engineering)은 이러한 확실한 협력을 기반으로한 형태로 기업에 도입되기 시작했습니다. 플랫폼은 애플리케이션 개발자, 데이터 과학자, 정보를 다루는 엔지니어(Information worker) 등 내부 고객의 작업을 촉진하고 가속화하기 위해 기본 기능, 프레임워크 및 경험을 선별하고 제공합니다. 특히 클라우드 컴퓨팅에서 플랫폼은 빠른 제품 출시, 인프라 간 이동성, 더 안전하고 탄력적인 제품, 개발자 생산성 향상 등 클라우드가 오랫동안 약속한 가치를 실현하는데 도움이 되었습니다.

이 백서는 기업의 리더, 아키텍트 및 플랫폼 팀 리더가 클라우드 컴퓨팅을 위한 기업 내부 플랫폼을 지지하고, 조사하고, 계획할 수 있도록 지원하고자 합니다. 플랫폼은 실제로 기업의 실제 가치 흐름에 큰 영향을 미치지만, 표면적으로는 간접적으로만 영향을 받는 것으로 보이기 때문에 플랫폼 팀의 장기적인 지속 가능성과 성공을 위해서는 경영진의 합의와 지원이 필수적입니다. 이 백서에서는 플랫폼의 가치가 무엇인지, 그 가치를 측정하는 방법, 가치를 극대화하는 플랫폼 팀을 구현하는 방법에 대해 논의함으로써 경영진 및 플랫폼 사용자 등 관계자들의 지원이 가능하게 할 것입니다.



## 목차

1. 왜 플랫폼인가요?
2. 플랫폼이란 무엇인가요?
3. 성공적인 플랫폼의 속성
4. 성공적인 플랫폼 팀의 속성
5. 플랫폼을 구현할 때의 도전 과제
6. 어떻게 플랫폼의 성공을 측정할 수 있나요?
7. 플랫폼의 기능들



## 왜 플랫폼인가요?

플랫폼과 플랫폼 엔지니어링은 오늘날 클라우드 컴퓨팅 세계에서 인기 있는 주제입니다. 플랫폼 구축에 대한 정의, 기술 및 측정에 대해 알아보기 전에 먼저 플랫폼이 제공하는 가치에 대해 살펴보는 것이 중요합니다.

지난 2\~3년 동안의 프로세스 개선으로 소프트웨어 애플리케이션 및 제품(Product) 팀의 민첩성이 크게 향상되어 컴퓨팅, 네트워크, 스토리지와 같은 인프라는 물론 빌드, 테스트, 배포, 관찰 가능성(Observability)과 같은 개발자를 위한 유연한 서비스 제공을 할 수 있게 되었습니다. 이러한 자율성과 프로세스 개선은 서비스 지원에 대한 책임을 점차 제품 팀으로 이전하는 효과도 가져왔으며, 제품 팀은 인프라 문제에 점점 더 많은 시간과 에너지를 소비하고 조직과 관련된 가치를 창출하는 데 더 많은 시간을 할애할 수 밖에 없게 되었습니다.

제공(Delivery, `역자: 일반적으로 한국에서는 현재 기준으로 DevOps 팀에서 주로 담당`) 팀이 핵심 업무에 다시 집중하고 조직 전반에서 중복되는 노력을 줄이려는 열망으로 인해 기업들은 클라우드 네이티브 컴퓨팅을 위한 플랫폼을 구현하게 되었습니다. 플랫폼에 투자함으로써 기업은 다음과 같은 이점을 얻을 수 있습니다:

1. 제품 팀의 업무 부하를 줄여 제품 개발 및 배포를 보다 빠르게 합니다.
2. 플랫폼 기능을 구성하고 관리할 전문가를 전담 배치하여 플랫폼 기능에 의존하는 제품의 안정성과 복원력 향상 시킵니다.
3. 기업 내 여러 팀에서 플랫폼 도구와 지식을 재사용하고 공유하여 제품 개발 및 제공을 가속화합니다.
4. 플랫폼 기능과 이를 둘러싼 사용자, 도구 및 프로세스를 관리하여 제품 및 서비스의 보안, 규제 및 기능 문제 위험을 줄입니다.
5. 사용자 경험에 대한 제어를 유지하면서 퍼블릭 클라우드 및 기타 관리형 제공업체에 구현을 위임하여 비용 효율적이고 생산적으로 서비스를 사용할 수 있도록 지원합니다.

이러한 이점들은 부분적으로는 소수의 플랫폼 팀이 많은 제품 팀에 서비스를 제공하여 그 영향력을 확대하기 때문에 발생합니다. 플랫폼 팀이 공통적으로 기능 관리를 통합하여 거버넌스를 쉽게 이용할 수 있게 하고 또한 무엇보다도 사용자 인터페이스와 경험을 중요하게 생각하는 조직이기 때문입니다.

플랫폼 전문가로 구성된 팀은 제품 팀에 요구되는 공통 업무를 줄여줄 뿐만 아니라 해당 제품에 사용되는 플랫폼 기능을 최적화합니다. 또한 플랫폼 팀은 전사적으로 광범위하게 사용되는 일련의 기존 패턴, 지식 및 도구를 유지 관리하여 개발자가 동일한 기반 위에 구축된 다른 팀과 제품에 신속하게 기여할 수 있도록 지원합니다. 또한 공유 플랫폼 패턴을 통해 템플릿, 패턴 및 기능에 거버넌스 및 제어 기능을 포함할 수 있습니다. 마지막으로, 플랫폼 팀은 제공업체를 통합하고 제공 서비스에 일관된 경험을 제공하기 때문에 데이터베이스, ID 액세스, 인프라 운영 및 앱 수명주기와 같이 기본적이며 CSP(Cloud Service Provider) 별로 특화되지 않은 기능들을 사용하기 위해서(`역자 생각: Lock in에 대해서 우려`) 퍼블릭 클라우드 및 서비스 제공업체를 이용할 수 있습니다.



## 플랫폼이란 어떤걸까요??

클라우드 네이티브 컴퓨팅을 위한 플랫폼은 플랫폼 사용자의 필요에 따라 정의되고 제공되는 기능의 통합 모음입니다. 플랫폼은 광범위한 애플리케이션 및 사용 사례에 대한 일반적인 기능과 서비스를 획득하고 통합하기 위한 일관된 경험을 보장하는 횡단 계층(cross-cutting layer, `역자: 계층간에 서로 영향을 주고 받을 수 있음 / 의존성에 가깝지만 여기서는`` `**`단일 사용자 채널`**`에 가까운 용어로 사용함` / [자세히 링크](https://zetawiki.com/wiki/%ED%9A%A1%EB%8B%A8\_%EA%B4%80%EC%8B%AC%EC%82%AC))  입니다. 좋은 플랫폼은 웹 포털, 프로젝트 템플릿 및 셀프 서비스 API와 같은 기능 및 서비스를 사용하고 관리하기 위한 일관된 사용자 경험을 제공합니다.

Atlassian\[[1](https://www.atlassian.com/devops/frameworks/team-topologies)]에 따르면, "플랫폼 팀은 오버헤드가 거의 없이 수많은 스트림 정렬 \[제품] 팀에서 사용할 수 있는 기능을 만듭니다.... 플랫폼 팀은 스트림 정렬 \[제품] 팀의 리소스 및 작업 부하를 최소화합니다... 플랫폼 팀은 다양한 사용자 경험 또는 제품에 걸쳐 일관된 경험을 만들 수 있습니다."라고 설명합니다.

마틴 파울러와 에반 보처\[[2](https://martinfowler.com/articles/talk-about-platforms.html)]에 따르면, "디지털 플랫폼은 하나의 매력적인 내부 제품으로 셀프 서비스 API, 도구, 서비스, 지식 및 지원을 잘 정리해서 제공합니다. 자율(Autonomous, `역자: 일종의 셀프 서비스 들로 인해서 제공 팀이 직접 서비스들을 제공하지 않아도 되는 형태`) 제공 팀은 플랫폼을 활용하여 조정을 줄이면서 더 빠른 속도로 제품 기능을 제공할 수 있습니다."라고 설명합니다.

플랫폼에서 지원하는 특정 기능 및 시나리오는 이해관계자와 사용자의 요구에 따라 결정되어야 합니다. 플랫폼이 이러한 필수 기능을 제공하지만, 플랫폼 팀이 항상 직접 구현해서는 안 된다는 점에 유의해야 합니다. 관리형 서비스 제공 업체나 전담 내부 팀은 지원 구현을 유지 관리할 수 있지만, 플랫폼을 통해 제공되는 구현 전반에 일관성을 제공하고 조직의 요구 사항을 충족하는 가장 합리적인 팀은 플랫폼 팀이어야  합니다. 예를 들어, 매우 간단한 '플랫폼'은 \[[3](https://teamtopologies.com/key-concepts-content/what-is-a-thinnest-viable-platform-tvp)]에 설명된 대로 제공업체의 기능을 프로비저닝하기 위한 표준 운영 절차에 대한 링크가 있는 위키 페이지일 수 있습니다.

이러한 플랫폼은 기업의 내부 사용자만을 대상으로 하기 때문에 내부 플랫폼이라고 부르는 경우가 많습니다.

플랫폼은 이전 패러다임(`역자 생각: DevOps 그리고 SRE 의 트렌드를 의미`, [설명](https://osckorea.tistory.com/173))보다 애플리케이션별 로직에서 지원 기능을 분리하기 때문에 클라우드 네이티브 아키텍처와 특히 밀접하게 연관되어 있습니다. 클라우드와 같은 환경에서는 리소스와 기능이 독립적으로 관리되고 사용자 지정 비즈니스 구성 요소와 통합되는 경우가 많으며, 이러한 리소스에는 데이터베이스 및 개체 저장소, 메시지 큐 및 브로커, 관찰 가능성 수집기(collectors, `역자: 익스포터들을 의미`) 및 대시보드, 사용자 디렉터리 및 인증 시스템, 작업 실행자 및 조정자(reconcilers) 등이 포함될 수 있습니다. 내부 플랫폼은 이러한 리소스를 애플리케이션과 시스템에 쉽게 통합할 수 있는 방식으로 엔터프라이즈 팀에 제공합니다.



## 플랫폼 성숙도

가장 기본적인 내부 플랫폼은 파이프라인 러너, 데이터베이스 시스템 또는 시크릿(Secret) 저장소와 같은 개별 서비스를 사용하기 위한 일관된 환경을 제공합니다. 내부 플랫폼이 성숙해짐에 따라 웹 애플리케이션 개발이나 데이터 분석과 같은 주요 시나리오를 위한 셀프 서비스 가능한 템플릿(일반적으로 MLOps)과 같은 서비스 구성도 제공합니다.

기업이 플랫폼을 통해 만날 수 있는 사용 사례는 다음과 같이 진행될 수 있습니다.

1. 제품 개발자는 필요에 따라 기능을 프로비저닝하여 컴퓨팅, 스토리지, 데이터베이스 또는 신원 확인(ID)과 같은 시스템을 즉시 사용할 수 있습니다.
2. 제품 개발자는 필요에 따라 서비스 공간을 프로비저닝하여 파이프라인 및 작업을 실행하고, 아티팩트 및 구성을 저장하고, 원격 측정을 수집하는 데 사용할 수 있습니다.
3. 타사 소프트웨어의 관리자는 필요에 따라 데이터베이스와 같은 필수 의존 요소를 프로비저닝하고 해당 소프트웨어를 쉽게 설치하고 실행할 수 있습니다.
4. 제품 개발자는 웹 개발이나 MLOps와 같은 특정 시나리오에 필요한 런타임 및 개발 시간 서비스를 결합한 템플릿이 갖춰진 완전한 환경에서 프로비저닝할 수 있습니다.
5. 제품 개발자와 관리자는 자동 계측 및 표준 대시보드를 통해 배포된 서비스의 기능, 성능, 비용을 모니터링할 수 있습니다.

내부 플랫폼은 개별 기능 또는 기능 세트에 대해 규정을 준수할 뿐만 아니라 일관된 경험을 제공함으로써 궁극적으로 사용자에게 가치 있는 제품을 보다 쉽고 효율적으로 제공할 수 있도록 지원합니다.

{{% pageinfo color="info" %}}
Please refer to the [Platform Engineering Maturity Model](https://tag-app-delivery.cncf.io/ko/whitepapers/platform-eng-maturity-model/) created after this paper was originally published.
{{% /pageinfo %}}

## 플랫폼의 속성

플랫폼이 무엇이며 조직이 플랫폼을 구축하려는 이유를 충분히 알아봤으니 다음으로는 플랫폼이 성공에 영향을 미치는 몇 가지 주요 속성을 파악해 보겠습니다.

1. **제품으로서의 플랫폼.** 플랫폼은 사용자의 요구 사항을 충족하기 위해 존재하며, 다른 소프트웨어 제품과 마찬가지로 이러한 요구 사항을 기반으로 설계되고 발전되어야 합니다. 플랫폼은 제품 팀 전반에서 가장 일반적인 사용 사례를 지원하는 데 필요한 기능을 제공해야 하며, 단일 팀에서만 사용하는 특정 기능보다 이러한 기능에 우선 순위를 두어 제공되는 가치를 극대화해야 합니다.
2. **사용자 경험.** 플랫폼은 일관된 인터페이스를 통해 기능을 제공하고 사용자 경험에 집중해야 합니다. 플랫폼은 사용자가 있는 곳에서 사용자를 만나기 위해 노력해야 하며, 이는 GUI, API, 커맨드 라인(command-line) 도구, IDE 및 포털의 통합을 의미할 수 있습니다. 예를 들어, 플랫폼은 일반적으로 애플리케이션 배포 기능을 제공합니다. 개발자는 IDE를 통해 이러한 기능을 사용할 수 있고, 테스터는 커맨드 라인 도구를 사용할 수 있으며, 제품 소유자는 GUI 기반 웹 포털을 사용할 수 있습니다.
3. **문서화 및 온보딩.** 성공적인 소프트웨어 제품의 핵심 요소는 문서화입니다. 사용자가 플랫폼의 제품을 사용하려면 문서와 예제가 필요합니다. 플랫폼은 사용자의 요구 사항을 충족하는 적절한 문서와 함께 제공되어야 합니다. 또한 사용자가 필요한 플랫폼 서비스를 빠르고 간단하게 사용할 수 있도록 새로운 프로젝트의 온보딩을 가속화할 수 있는 도구를 제공해야 합니다. 예를 들어, 플랫폼은 쿠버네티스에서 웹 애플리케이션을 빌드, 스캔, 테스트, 배포 및 모니터링 하기 위해 재사용 가능한 형태의 서비스 공급망(supply chain) 워크플로우를 제공할 수 있습니다. 이러한 워크플로우는 초기 프로젝트 템플릿 및 문서와 함께 제공될 수 있으며, 종종 가장 빠르게 도입(Golden path)할 수 있는 번들 형태로 제공되기도 합니다.
4. **셀프 서비스.** 플랫폼은 셀프서비스가 가능해야 합니다. 사용자가 자율적으로 자동으로 기능을 요청하고 받을 수 있어야 합니다. 이 속성은 플랫폼 팀이 여러 제품 팀을 지원하고 필요에 따라 확장할 수 있도록 하는 핵심 요소입니다. 플랫폼 기능은 위에서 설명한 인터페이스를 통해 최소한의 수동 개입으로 필요에 따라 사용할 수 있어야 합니다. 예를 들어, 사용자가 커맨드 라인 도구를 실행하거나 웹 포털에서 양식을 작성하여 데이터베이스를 요청하고 해당 위치 및 자격 증명(credentials)을 받을 수 있어야 합니다.
5. **사용자의 작업 부하 감소.** 플랫폼의 필수 목표는 제품 팀의 작업 부하를 줄이는 것입니다. 플랫폼은 구현 세부 사항을 요약하고 아키텍처에서 발생할 수 있는 모든 복잡성을 숨겨야 합니다. 예를 들어, 플랫폼은 특정 서비스를 클라우드 제공업체에 위임할 수 있지만 사용자는 이러한 세부 사항에 노출되어서는 안 됩니다. 동시에 플랫폼은 사용자가 필요에 따라 특정 서비스를 구성하고 관찰할 수 있도록 허용해야 합니다. 사용자는 플랫폼에서 제공하는 서비스 운영에 대한 책임을 져서는 안 됩니다. 예를 들어, 사용자는 종종 데이터베이스가 필요할 수 있지만 데이터베이스 서버를 관리할 필요가 없어야 합니다.
6. **선택 사항 및 구성 가능.** 플랫폼은 제품 개발의 효율성을 높이기 위한 것이므로 장애물이 되어서는 안 됩니다. 플랫폼은 구성이 가능해야 하며 제품 팀이 플랫폼의 일부만 사용할 수 있어야 합니다. 또한 필요한 경우 제품 팀이 플랫폼 외부에서 자체 기능을 제공하고 관리할 수 있어야 합니다. 예를 들어, 플랫폼에서 그래프 데이터베이스(`역자: 예를 들자면 Neo4j`)를 제공하지 않지만 제품에 필요한 경우, 제품 팀이 직접 그래프 데이터베이스를 프로비저닝하고 운영할 수 있어야 합니다.
7. **보안은 기본.** 플랫폼은 기본적으로 안전해야 하며 조직에서 정의한 규칙과 표준에 따라 규정 준수 및 유효성 검사를 보장하는 기능을 제공해야 합니다.

## 플랫폼 팀의 속성

플랫폼 팀은 웹 포털, 사용자 지정(custom) API, 빠른 도입을 위한 템플릿과 같은 플랫폼 기능에 대한 인터페이스와 사용자 경험을 담당합니다. 플랫폼 팀은 인프라를 구현하고 서비스를 지원하는 팀과 협력하여 일관된 경험을 규정하고, 다른 한편으로는 제품 및 사용자 팀과 협력하여 피드백을 수집하는 한편 이러한 경험이 실제로 사용자의 요구 사항을 충족하는지 확인합니다.

다음은 플랫폼 팀이 담당해야 하는 업무입니다.

1. 플랫폼 사용자 요구 사항 조사 및 기능 로드맵 수립
2. 플랫폼이 제안하는 가치를 마케팅, 홍보 지원
3. 포털, API, 문서 및 템플릿, 커맨드 라인(CLI) 도구 등 기능 및 서비스를 사용하고 관찰하기 위한 인터페이스를 관리 및 개발

가장 중요한 것은 플랫폼 팀이 플랫폼에서 제공하는 기능과 인터페이스를 알리고 지속적으로 개선하기 위해 플랫폼 사용자의 요구사항을 파악해야 한다는 것입니다. 사용자 요구 사항을 파악하는 방법에는 사용자 인터뷰, 양방향 해커톤, 이슈 트래커 및 설문조사, 관찰 가능성 도구를 통한 사용 현황 직접 관찰 등이 있습니다. 예를 들어, 플랫폼 팀은 사용자가 기능 요청을 제출할 수 있는 양식을 게시하고, 로드맵 회의를 주도하여 예정된 기능을 공유하고, 사용자의 사용 패턴을 검토하여 우선 순위를 설정할 수 있습니다.

플랫폼은 내부로부터(Inbound)의 피드백과 면밀한 설계를 가지고 있어야 하고, 다른 측면으로는 적극적으로 외부(Outbound)에 마케팅적으로 알려야 하고 지원 받아야 합니다. 플랫폼이 진정으로 사용자 요구사항에 맞게 구축되었다면 사용자들은 플랫폼에서 제공하는 기능등을 기꺼이 사용할 것입니다. 플랫폼 팀이 사용자의 사용을 유도하는 몇 가지 방법으로는 광범위한 공지, 매력적인 데모, 정기적인 피드백 및 커뮤니케이션 세션 등의 내부 마케팅 활동을 들 수 있습니다. 여기서 핵심은 사용자가 있는 곳에서 사용자를 만나고 플랫폼에 참여하고 혜택을 누릴 수 있는 과정을 안내하는 것입니다.

플랫폼 팀이 반드시 컴퓨팅, 네트워크, 스토리지 또는 기타 서비스를 운영할 필요는 없습니다. 사실 내부 플랫폼은 가능한 한 외부에서 제공하는 서비스와 기능에 의존해야 하며, 플랫폼 팀은 관리 공급업체나 내부 인프라 팀에서 사용할 수 없는 경우에만 자체 기능을 구축하고 유지 관리해야 합니다. 대신 플랫폼 팀은 플랫폼에서 제공하는 서비스 및 기능에 대한 인터페이스(예: GUI, CLI, API) 및 사용자 경험에 대해서 확실히 책임을 지고 유지 관리해야 합니다.

예를 들어, 플랫폼의 웹 페이지에서 앱의 신원 인증(ID)을 제공하는 버튼에 대해 설명하고 제공할 수 있으며, 실제로해당 기능에 대한 구현은 클라우드에서 호스팅되는 ID 서비스(`역자: 예를 들자면 IAM관련 서비스`)를 통해 이루어질 수 있습니다. 내부 플랫폼 팀이 웹 페이지와 API를 관리할 수 있지만 실제 서비스 구현은 관리하지 않을 수 있습니다. 플랫폼 팀은 일반적으로 필요한 기능을 다른 곳에서 사용할 수 없는 경우에만 자체 기능을 만들고 유지 관리하는 것을 고려해야 합니다.



## 플랫폼의 당면 과제

플랫폼은 많은 가치를 약속하지만, 구현자가 염두에 두어야 할 다음과 같은 과제도 있습니다.

1. 플랫폼 팀은 플랫폼을 제품처럼 취급하고, 사용자와 함께 개발해야 합니다.
2. 플랫폼 팀은 우선 순위와 초기 파트너 애플리케이션 팀을 신중하게 선택해야 합니다.
3. 플랫폼 팀은 기업 경영진의 지원을 얻고, 비지니스 가치 흐름에 미치는 영향을 보여줘야 합니다.

가장 중요한 것은 플랫폼을 고객 대상 제품으로 취급하고, 플랫폼의 성공이 사용자와 제품의 성공에 직접적으로 좌우된다는 점을 인식하는 것입니다. 따라서 플랫폼 팀은 애플리케이션 팀 및 다른 사용자와 협력하여 플랫폼의 기능과 사용자 경험의 우선 순위를 정하고, 계획하고, 구현하고, 반복하는 것이 중요합니다. 피드백 없이 기능과 경험을 공개하거나 탑다운 방식에 의존하여 도입을 추진하는 플랫폼 팀은 사용자의 저항과 반발을 불러일으키고 결국 약속한 가치를 상당 부분 놓칠 가능성이 높습니다. 이를 방지하기 위해 플랫폼 팀은 처음부터 제품 관리자를 포함시켜 로드맵을 공유하고, 피드백을 수집하며, 플랫폼 사용자의 요구 사항을 전반적으로 이해하고 반영해야 합니다.

플랫폼을 도입할 때는 우선적으로 지원해야 할 기능과 경험을 선택하는 것이 중요합니다. 파이프라인, 데이터베이스 및 관찰 가능성과 같이 자주 필요하지만 차별화되지 않은 기능을 먼저 시작하는 것이 좋습니다. 플랫폼 팀은 참여도가 높고 숙련된 소수의 애플리케이션 팀에 우선적으로 주력할 수도 있습니다. 이러한 팀의 상세한 피드백은 첫 번째 플랫폼 경험을 개선하고, 이러한 팀의 사람들은 나중에 플랫폼을 채택하는 사람들에게 플랫폼을 홍보하고 전파하는 데 도움을 줍니다.

마지막으로, 플랫폼팀은 기업의 경영진으로부터 지원을 신속하게 확보하는 것이 매우 중요합니다. 많은 기업 경영진은 IT 인프라를 주요 비지니스 가치 흐름과 동떨어진 비용으로 인식하고 IT 플랫폼에 할당되는 비용과 리소스를 제한하려고 하기 때문에 구현이 제대로 이루어지지 않아 플랫폼 엔지니어팀의 의욕을 꺽을 수 있고 또한 플랫폼 사용자들을 떠나게 만들 수 있습니다. 이를 방지하기 위해 플랫폼 팀은 최종 제품 및 비지니스 가치 흐름에 직접적인 영향을 미친다는 것을 입증하고, 이를 통해서 제품 팀과 전략적인 협력 관계임을 보여주어야 합니다.



## 플랫폼팀을 어떻게 도와줄 것인가?

이러한 당면 과제들을 통해 볼 때 플랫폼 팀은 다양한 책임에 가지고 있으며, 이는 과중한 업무량으로 이어진다는 것을 알 수 있습니다. 애플리케이션 팀과 마찬가지로 플랫폼 팀도 지원해야 하는 사용자와 팀의 수와 다양성이 증가함에 따라 이러한 당면 과제들은 더욱 커집니다.

플랫폼 팀의 에너지를 특정 비즈니스 역량에 집중하는 것은 매우 중요합니다. 플랫폼 팀의 업무 부담을 줄이는 방법에는 다음이 포함됩니다.

1. 관리형 제공업체에서 이미 구현된 기능을 쓰기 보다 가장 가벼운 형태([TVP](platform\_whitepaper.md#glossary), thinnest viable platform)로 구동할 수 있는 플랫폼 계층을 구축하기 위해 노력해야 합니다.
2. 오픈 소스 프레임워크 및 툴킷(toolkits)을 이용해서 애플리케이션 팀이 사용할 문서, 템플릿 및 구조(compositions)를 만듭니다.
3. 플랫폼 팀이 도메인(Domain)과 고객 수에 맞게 적절한 인력을 확보하도록 합니다.



## 어떻게 플랫폼의 성공을 측정할 수 있나요?

기업은 플랫폼 형태로의 도입 또는 전환이 위에서 설명한 가치와 속성을 제공하고 있는지 측정하고자 할 것입니다. 또한 이 백서 전체에서 내부 플랫폼을 제품으로 취급하는 것이 중요하며, 우수한 제품 관리는 제품 성능의 정량적, 정성적 측정에 달려 있다고 강조했습니다. 이러한 요구 사항을 충족하기 위해 내부 플랫폼 팀은 지속적으로 사용자 피드백을 수집하고 사용자 활동을 측정해야 합니다.

하지만 내부 플랫폼의 다른 측면과 마찬가지로 플랫폼 팀은 필요한 피드백을 수집하기 위해 가능한 최소한의 노력을 기울여야 합니다. 여기서는 몇 가지 지표를 제안하지만, 초기에는 사용자 행동에 대한 간단한 설문조사와 분석이 가장 유용할 수 있습니다.

기업과 플랫폼 팀이 플랫폼의 영향을 이해하는 데 도움이 되는 지표의 범주는 다음과 같습니다:

### 사용자 만족도 및 생산성

많은 플랫폼이 추구하는 첫 번째 품질은 생산성을 높이기 위해 사용자 경험을 개선하는 것입니다. 사용자 만족도와 생산성을 반영하는 지표에는 다음이 포함됩니다

* 활성 사용자 및 유지율(Retention): 프로비저닝된 기능 수 및 사용자 증가/이탈 포함
* "제품에 대한 사용자 만족도를 측정하는 "순추천지수(NPS, Net Promoter Score)" 또는 기타 설문조사
* SPACE 프레임워크에서 논의된 것과 같은 개발자 생산성에 대한 지표\[[4](https://queue.acm.org/detail.cfm?id=3454124)]

### 조직 효율성

많은 플랫폼에서 이루고자하는 또 다른 효과는 대규모 사용자 기반에 공통의 요구 사항을 효율적으로 제공하는 것입니다. 이는 사용자 셀프 서비스를 활성화하고 일일이 수작업으로 진행해야 하는 단계와 사람의 개입을 줄임과 동시에 안전과 규정 준수를 보장하는 정책을 구현함으로써 달성되는 경우가 많습니다. 공통 작업을 줄이는 데 있어 플랫폼의 효율성을 측정하려면 다음과 같은 측정 항목을 고려할 수 있습니다.

* 데이터베이스 또는 테스트 환경과 같은 서비스 또는 기능 요청부터 이행까지의 지연 시간
* 새로운 서비스를 빌드하고 프로덕션 환경에 배포하는 데 걸리는 지연 시간
* 새로운 사용자가 제품에 대한 첫 번째 코드 변경 사항을 제출하는 데 걸리는 시간

### 제품 및 기능 제공

내부 플랫폼의 궁극적인 목표는 고객에게 비즈니스 가치를 더 빠르게 제공하는 것이므로, 비즈니스 자체의 제품 및 기능 릴리스에 대한 영향을 측정하면 플랫폼의 목표가 달성되고 있음을 알 수 있습니다. Google의 DevOps 연구 및 평가(DORA) 연구소는 \[[5](https://cloud.google.com/blog/products/devops-sre/the-2019-accelerate-state-of-devops-elite-performance-productivity-and-scaling?hl=en)] 다음 메트릭을 추적할 것을 제안합니다.

* 배포 빈도
* 변경에 소요되는 시간(Lead time)
* 장애 후 서비스 복원 시간
* 변경 실패율

일반적으로 플랫폼 팀의 핵심 목표는 인프라 및 기타 IT 기능을 기업의 가치 흐름, 즉 제품에 맞춰 조정하는 것입니다. 따라서 궁극적으로 기업의 제품과 애플리케이션의 성공이 플랫폼의 성공을 가늠하는 진정한 척도입니다.

## 플랫폼의 기능들

앞서 설명한 것처럼 클라우드 네이티브 컴퓨팅을 위한 플랫폼은 여러 지원 제공업체의 기능과 서비스를 함께 혼합하여 제공합니다. 이러한 제공업체는 같은 기업 내의 다른 팀일 수도 있고 클라우드 서비스 제공업체와 같은 타사일 수도 있습니다. 간단히 말해, 플랫폼은 기본 기능 제공업체와 애플리케이션 개발자와 같은 플랫폼 사용자를 연결하고, 그 과정에서 보안, 성능, 비용 거버넌스, 일관된 경험에 대해 원하는 모범 사례를 구현하고 시행합니다. 다음 그래픽은 제품, 플랫폼, 기능 제공업체 간의 관계를 보여줍니다.

<figure><img src="https://github.com/Cloud-Native-Platform-Engineering/cnpe-community/blob/main/website/content/ja/wgs/platforms/whitepaper/assets/platforms-def.drawio.png" alt=""><figcaption><p>제품과 플랫폼 그리고 기능 제공업체 간의 관계 그래프</p></figcaption></figure>

이 백서에서는 우수한 플랫폼과 플랫폼 팀을 구성하는 방법에 중점을 두었으며, 이제 마지막 섹션에서는 플랫폼이 실제로 제공할 수 있는 기능에 대해 설명하고자 합니다. 이 목록은 플랫폼 구축 담당자를 안내하기 위한 것으로, 일반적으로 클라우드 네이티브 애플리케이션에 필요한 기능을 포함하고 있습니다. 하지만 앞서 언급했듯이 좋은 플랫폼은 사용자의 요구 사항을 반영하므로 궁극적으로 플랫폼 팀은 사용자와 함께 플랫폼이 제공하는 기능을 선택하고 우선 순위를 정해야 합니다.

기능들은 도메인의 특성에 따라 여러가지로 특성 및 속성이 나누어질 수 있습니다. 예를 들어, 관찰 가능성에는 메트릭, 추적 및 로그를 수집 및 게시하고 비용 및 리소스 사용량을 모니터링하기 위한 기능이 포함될 수 있습니다. 이 때 조직에서는 각 기능 또는 요소의 필요성과 우선순위를 고려해서 적용해야 합니다. 추후 CNCF 발행물은 각 도메인에 대해 더 확장해서 배포할 수 있습니다.

다음은 클라우드 네이티브 컴퓨팅을 위한 플랫폼을 구축할 때 고려해야 할 기능 영역입니다.

1. **웹 포털**: 제품 및 기능을 관찰하고 할당 및 배포 관리(provisioning)함
2. **API(및 CLI)**: 제품 및 기능을 자동으로 할당 및 배포 관리(provisioning)함
3. **가장 빠른 도입을 위한(Golden Path) 템플릿 및 문서**:  제품에서 기능을 최적으로 사용할 수 있도록 지원
4. **구축 및 테스트를 위한 자동화**: 서비스 및 제품에 해당
5. **전달(delivering) 및 검증을 위한 자동화**: 서비스 및 제품에 해당
6. **개발 환경**:  사용할 수 있도록 설치 구성된(hosted) IDE와 원격 연결 도구 제공
7. **관찰 가능성**: 계측 및 대시보드를 사용하여 서비스 및 제품을 모니터링(기능, 성능 및 비용 관찰 포함)
8. **인프라(Infrastructure) 서비스**: 런타임이 동작가능한 컴퓨터, 프로그래밍에 사용할 네트워크, 블록 및 볼륨 스토리지를 제공
9. **데이터 서비스**: 데이터베이스, 캐시, 객체 저장소, 메시징 및 이벤트 서비스(서비스 브로커, 큐, 이벤트 패브릭을 포함) 제공
10. **사용자 인증 및 시크릿(Secret) 관리 서비스**: 서비스 및 사용자 ID 및 권한 부여, 인증서 및 키 발급, 정적 시크릿 저장소 제공
11. **보안 서비스**:  코드 및 아티팩트의 정적 분석, 런타임 분석, 정책 적용을 제공
12. **아티팩트(Artifact ) 저장소**: 컨테이너 이미지 및 언어별 패키지, 사용자 지정 바이너리 및 라이브러리, 소스 코드의 저장 제공

다음 표는 독자들이 각 기능을 기존 CNCF 또는 CDF 프로젝트와 느슨하게 연관시켜 파악하는 데 도움을 주기 위한 것입니다.

| 기능                     | 설명                                                                                                       | CNCF/CDF 프로젝트 예시                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| 프로비저닝 및 관찰 기능을 위한 웹 포털 | 문서, 서비스 카탈로그 및 프로젝트 템플릿을 게시합니다. 시스템 및 기능에 대한 원격 분석을 게시                                                   | Backstage, Skooner, Ortelius                                                                             |
| 자동 프로비저닝 기능을 위한 API    | 자동으로 생성, 업데이트, 삭제 및 관찰 기능을 위한 구조화된 형식                                                                    | Kubernetes, Crossplane, Operator Framework, Helm, KubeVela                                               |
| 최적(Golden) 경로 템플릿 및 문서 | 신속한 프로젝트 개발을 위해 잘 통합된 코드와 기능으로 구성된 템플릿을 제공                                                               | ArtifactHub                                                                                              |
| 제품 구축 및 테스트를 위 한 자동화   | 디지털 제품 및 서비스의 빌드 및 테스트를 자동화                                                                              | Tekton, Jenkins, Buildpacks, ko, Carvel                                                                  |
| 서비스 전달과 확인을 자동화        | 서비스의 전달 및 확인을 자동화                                                                                        | Argo, Flux, Keptn, Flagger, OpenFeature                                                                  |
| 개발 환경                  | 애플리케이션과 시스템의 연구 및 개발을 지원                                                                                 | Devfile, Nocalhost, Telepresence, DevSpace                                                               |
| 애플리케이션의 관측가능성          | 애플리케이션을 계측하고, 원격 측정을 수집 및 분석하고, 이해 관계자에게 정보를 게시                                                          | OpenTelemetry, Jaeger, Prometheus, Thanos, Fluentd, Grafana, OpenCost                                    |
| 인프라 서비스                | 애플리케이션 코드 실행, 애플리케이 션 구성 요소 연결 및 애플리케이션의 데이터 유지                                                          | Kubernetes, Kubevirt, Knative, WasmEdge CNI, Istio, Cilium, Envoy, Linkerd, CoreDNS Rook, Longhorn, Etcd |
| 데이터 서비스                | 애플리케이션을 위한 구조화된 데이터 유지                                                                                   | TiKV, Vitess, SchemaHero                                                                                 |
| 메시징 및 이벤트 서비스          | 애플리케이션이 서로 비동기적으로 통신할 수 있도록 지원                                                                           | Strimzi, NATS, gRPC, Knative, Dapr                                                                       |
| 신원인증 및 시크릿(Secret) 서비스 | 워크로드에 리소스와 기능을 사용할 수 있는 로케이터와 암호가 있는지 확인합니다. 서비스가 다른 서비스에 자신을 식별할 수 있도록 지원                               | Dex, External Secrets, SPIFFE/SPIRE, Teller, cert-manager                                                |
| 보안 서비스                 | 런타임 동작을 관찰하고 이상 징후 를 보고/수정합니다. 빌드 및 아티팩트에 취약점이 없는지 확인합니다. 엔터프라이즈 요구 사항에 따라 플랫폼에서 활동을 제한하고 이상 징후를 알리거나 수정 | Falco, In-toto, KubeArmor, OPA, Kyverno, Cloud Custodian                                                 |
| 아티팩트 스토리지              | 프로덕션에서 사용할 수 있도록 빌드된 아티팩트를 저장, 게시 및 보호합니다. 타사 아티팩트를 캐시하고 분석합니다. 그리고 소스 코드를 저장하는 기능도 제공                   | ArtifactHub, Harbor, Distribution, Porter                                                                |
