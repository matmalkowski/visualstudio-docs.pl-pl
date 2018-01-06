---
title: "Struktury rozwiązania modelowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: "14"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3819227bbdfdd754166c886c9da0cc8bd727e94e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania
Aby skutecznie używanie modeli w opracowywanego projektu, członków zespołu musi mieć możliwość pracy w modelach różnych części projektu w tym samym czasie. W tym temacie sugeruje schemat podziału aplikacji na różne części odpowiadające warstwy ogólną diagram Tworzenie warstw.  
  
 Do uruchomienia w projekcie lub subproject szybko, warto stosowanej struktury projektu, który wybrano szablon projektu. W tym temacie opisano sposób tworzenia i użyj szablonu adresu.  
  
 W tym temacie założono, że pracujesz na projekt, który jest wystarczająco duży, aby wymagać kilku członków zespołu i prawdopodobnie ma kilka zespołów. Kod i modele projektu są przechowywane w systemie kontroli źródła takich jak [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Co najmniej jednym członkom zespołu tworzenie modeli za pomocą programu Visual Studio i innych członków zespołu można wyświetlić modeli przy użyciu innych wersji programu Visual Studio.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji narzędzia i modelowanie, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Struktura rozwiązania  
 W projekcie średnich i dużych struktury zespołu opiera się na strukturze aplikacji. Każdy zespół używa rozwiązania Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>Aby podzielić aplikację do warstwy  
  
1.  Podstawowa struktura rozwiązań w strukturze aplikacji, na przykład aplikacja sieci web, aplikacji usługi lub aplikacji komputerowych. Szereg typowych architektury opisanej w [Archetypes aplikacji w Przewodniku dotyczącym architektury aplikacji Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2.  Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, które będą nazywamy architektury rozwiązania. To rozwiązanie będzie służyć do tworzenia ogólnego projektu systemu. Modele, ale żaden kod nie będzie zawierać.  
  
     Dodaj zależności diagram do tego rozwiązania. Na diagramie zależności Rysuj architekturę, którą wybrano dla aplikacji. Na przykład diagramu mogą być wyświetlane w tych warstwach i zależności między nimi: prezentacji; Logika biznesowa; i dane.  
  
4.  Utwórz oddzielne rozwiązania Visual Studio dla poszczególnych warstw w diagram architektury zależności.  
  
     Te rozwiązania będzie używany do opracowywania kodu warstw.  
  
5.  Tworzenie modeli reprezentujących projektów warstwy i pojęcia, które są wspólne dla wszystkich warstw. Rozmieść modele, aby wszystkie modele wynika z architektury rozwiązania, a odpowiednie modele wynika z każdej warstwy.  
  
     Można to osiągnąć przy użyciu jednej z poniższych procedur. Pierwszy alternatywnej tworzy projekt modelowania osobne dla każdej warstwy, a drugi tworzy projekt modelowania jednego udostępnionego między warstwami.  
  
    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Aby użyć projektu modelowania osobne dla każdej warstwy  
  
    1.  Utwórz projekt modelowania w poszczególnych rozwiązaniach warstwy.  
  
         Ten model zawiera diagramy, na których opis wymagań i projektowania tej warstwy. Może również zawierać diagramy zależności, których wyświetlane są zagnieżdżone warstwy.  
  
         Istnieje już model dla każdej warstwy, a także modelu dla architektury aplikacji. Każdy model znajduje się w jego własnej rozwiązania. Dzięki temu członkowie zespołu nad warstw, w tym samym czasie.  
  
    2.  Do rozwiązania architektury Dodaj projekt modelowania poszczególnych rozwiązań do warstwy. Aby to zrobić, otwórz rozwiązanie architektury. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie Dodaj, a następnie kliknij przycisk **istniejący projekt**. Przejdź do projektu modelowania (.modelproj) w jedną warstwę rozwiązania.  
  
         Każdy model jest teraz widoczne w dwóch rozwiązań: rozwiązanie "home" oraz architektury rozwiązania.  
  
    3.  Do projektu modelowania poszczególnych warstw dodać diagram zależności. Uruchom kopię diagram architektury zależności. Możesz usunąć elementy, które nie są zależności na diagramie zależności.  
  
         Można również dodać diagramy zależności, które reprezentują szczegółowe strukturę tej warstwy.  
  
         Diagramy te są używane do weryfikacji kod, który został utworzony w tej warstwie.  
  
    4.  W rozwiązaniu architektura edytować wymagań i projektowania modeli wszystkich warstw w programie Visual Studio.  
  
         W poszczególnych rozwiązaniach warstwy opracowanie kod dla tej warstwy odwołujących się do modelu. Jeśli jesteś zawartości w celu opracowywania bez korzystania z tego samego komputera do aktualizacji modelu, można czytać modelu i Opracuj kodu za pomocą wersji programu Visual Studio nie może utworzyć modeli. Można również generowanie kodu na podstawie modelu w tych wersjach.  
  
     Ta metoda gwarantuje, że nie występują zakłócenia wystąpią przez deweloperów, którzy edytowanie modeli warstw w tym samym czasie.  
  
     Jednak ponieważ modele są oddzielone, jest trudne do odwoływania się do wspólnego pojęcia. Każdy model musi mieć własną kopię elementy, na których jest on zależny od innych warstw i architektura. Diagram zależności w każdej warstwie musi być zsynchronizowany z diagram architektury zależności. Jest trudne w utrzymaniu synchronizacji zmiany tych elementów, mimo że można rozwijać narzędzia w tym celu.  
  
    ###### <a name="to-use-a-separate-package-for-each-layer"></a>Aby użyć oddzielny pakiet dla każdej warstwy  
  
    1.  W rozwiązaniu dla poszczególnych warstw Dodaj projekt modelowania architektury. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **istniejący projekt**. Projekt modelowania pojedynczego jest teraz dostępna z każdej rozwiązania: projekt architektury i projektu tworzenia dla każdej warstwy.  
  
    2.  W modelu udostępnionego, należy utworzyć pakiet dla każdej warstwy: W Eksploratorze rozwiązań wybierz projekt modelowania. W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **pakietu**.  
  
         Każdy pakiet będzie zawierać diagramy zawierających opis wymagań i projektowania odpowiedniej warstwy.  
  
    3.  W razie potrzeby dodaj diagramy lokalnego zależności dla wewnętrznej struktury każdej warstwy.  
  
     Ta metoda umożliwia elementów projektu każdą warstwę można odwoływać się bezpośrednio do warstwy i architektura wspólne, od którego zależy.  
  
     Współbieżne roboczych na różnych pakietów mogą powodować niektóre konflikty, są one dość łatwe do zarządzania, ponieważ pakiety są przechowywane w oddzielnych plikach.
  
## <a name="creating-architecture-templates"></a>Tworzenie szablonów architektury  
 W praktyce rozwiązań programu Visual Studio nie zostanie utworzony w tym samym czasie, ale dodać je jako postępu projektu. Prawdopodobnie będziesz również użycie tej samej struktury rozwiązania w przyszłych projektów.  Aby ułatwić szybkie tworzenie nowych rozwiązań, można utworzyć szablon rozwiązania lub projektu. Tak, aby łatwo dystrybucji i zainstalować na innych komputerach, można przechwycić szablonu w programie Visual Studio integracji rozszerzenia (VSIX).  
  
 Na przykład jeśli często używane rozwiązania, które mają warstwy prezentacji, biznesowych i danych, można skonfigurować szablon, który spowoduje utworzenie nowych rozwiązań, które mają tej struktury.  
  
#### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania  
  
1.  [Pobierz i zainstaluj Kreatora eksportowania szablonu](http://go.microsoft.com/fwlink/?LinkId=196686), jeśli użytkownik ma nie zostało to zrobione.  
  
2.  Tworzenie struktury rozwiązania, który ma być używany jako punkt początkowy dla przyszłych projektów.  
  
3.  Na **pliku** menu, kliknij przycisk **Eksportuj szablon jako VSIX**. **Eksportuj szablon jako Kreator VSIX** otwiera.  
  
4.  Postępując zgodnie z instrukcjami w kreatorze Wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu i określ lokalizację danych wyjściowych.  
  
> [!NOTE]
>  Materiał w tym temacie jest pobieranej i paraphrased z programu Visual Studio narzędzi dotyczące architektury, napisane przez Visual Studio ALM Rangers, który jest współpraca między najbardziej ważnych specjaliści (MVP), Microsoft Services i programu Visual Studio Zespół produktu i modułów zapisujących. [Kliknij tutaj, aby pobrać pełny pakiet wskazówki.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Materiały pokrewne  
 [Organizowanie i zarządzanie modeli](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - wideo przez Clint Edmondson.  
  
 [Visual Studio narzędzi dotyczące architektury](../modeling/visual-studio-architecture-tooling-guidance.md) -dalsze wskazówki dotyczące zarządzania modeli w zespole  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
