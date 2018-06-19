---
title: Zapisywanie rejestratorów kilku-procesorów obsługujących | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a01fb5d47f390c311f119e669e7fdb75619b058
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572598"
---
# <a name="writing-multi-processor-aware-loggers"></a>Zapisywanie rejestratorów uwzględniających wiele procesorów
Zdolność [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mógł korzystać z wielu procesorów może zmniejszyć czas tworzenia projektu, ale również dodaje złożoności rejestrowanie zdarzeń kompilacji. W środowisku z jednym procesorem zdarzenia, wiadomości, ostrzeżenia i błędy przyjeździe rejestratora w sposób przewidywalne, sekwencyjnych. Jednak w środowisku wielu procesorów zdarzeń z różnych źródeł może pojawiają się w tym samym czasie lub poza kolejnością. Aby zapewnić w tym celu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zapewnia kilku-procesorów obsługujących rejestratora i nowy model rejestrowania i umożliwia utworzenie niestandardowej "przekazywanie rejestratorów."  
  
## <a name="multi-processor-logging-challenges"></a>Rejestrowanie wielu procesorów wyzwania  
 Podczas tworzenia jednego lub więcej projektów w systemie wieloprocesorowym lub wielordzeniowych [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zdarzenia kompilacji dla wszystkich projektów są generowane w tym samym czasie. Lawiny komunikaty o zdarzeniach może pojawić się u rejestratora, w tym samym czasie lub poza kolejnością. Ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestratora 2.0 nie jest przeznaczony do obsługi tej sytuacji, można przeciąży rejestratora i spowodować razy większa kompilacji, Rejestrator nieprawidłowe dane wyjściowe lub uszkodzony kompilacji. Aby rozwiązać te problemy, rejestratora (począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5) można przetworzyć zdarzenia sekwencji i korelowanie zdarzeń i ich źródła.  
  
 Można zwiększyć wydajność rejestrowania jeszcze więcej tworząc Rejestrator przekazujący niestandardowych. Rejestrator niestandardowych przekazujący działa jako filtr, umożliwiając przed utworzeniem, wybrać tylko zdarzenia, które chcesz monitorować. Gdy używasz Rejestrator przekazujący niestandardowych niechciane zdarzeń nie może przeciąży rejestratora, zajmowały dzienników lub wolno kompilacji razy.  
  
## <a name="multi-processor-logging-models"></a>Modele rejestrowanie wielu procesorów  
 Do zapewnienia problemy związane z procesorów kilku kompilacji [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsługuje dwa modele rejestrowania centralnej i rozproszone.  
  
### <a name="central-logging-model"></a>Model centralnego rejestrowania  
 W modelu centralnego rejestrowania pojedynczym wystąpieniu programu MSBuild.exe działa jako "centralnej węzła", i wystąpień podrzędnych węzła centralnej ("dodatkowej węzłów") Dołącz do centralnej węzeł, aby ułatwić wykonywanie zadań kompilacji.  
  
 ![Model rejestratora centralnego](../msbuild/media/centralnode.png "CentralNode")  
  
 Rejestratory różne typy, które dołączanie do węzła centralnej są określane jako "centralnej rejestratorów." Tylko jedno wystąpienie każdego typu rejestratora może zostać dołączona do centralnej węzła w tym samym czasie.  
  
 Podczas kompilacji pomocniczej węzłów trasy ich zdarzeń kompilacji do centralnej węzła. Węzeł centralnej kieruje jego zdarzeń, a także tych węzłów dodatkowej do co najmniej jednego z dołączonych rejestratorów centralnej. Rejestratory następnie utworzyć plików dziennika, które są oparte na danych przychodzących.  
  
 Chociaż tylko <xref:Microsoft.Build.Framework.ILogger> jest wymagane do zaimplementowania przez centralną rejestratora, zalecamy również stosowanie <xref:Microsoft.Build.Framework.INodeLogger> tak, aby rejestratora centralnego inicjuje z liczbą węzłów, które uczestniczą w kompilacji. Następujące przeciążenia z <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> wywołuje metodę, gdy aparat rejestratora.  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Wszystkie istniejące <xref:Microsoft.Build.Framework.ILogger>-rejestratorów oparte na może działać jako rejestratorów centralnej i dołączyć do kompilacji. Jednak centralnej rejestratorów bez jawnego obsługę scenariuszy rejestrowanie wielu procesorów i zdarzenia poza kolejnością może Przerwij kompilację lub generowania danych wyjściowych znaczenia.  
  
### <a name="distributed-logging-model"></a>Model rejestrowania rozproszonego  
 W modelu centralnego rejestrowania zbyt dużą ilość ruchu przychodzącego komunikatu może spowodować przeciążenie centralnej węzła, na przykład podczas tworzenia wielu projektów w tym samym czasie. To podkreślają zasobów systemowych i zmniejszyć wydajność kompilacji. Aby ułatwić ten problem, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsługuje model rejestrowania rozproszonych.  
  
 ![Model rejestrowania rozproszonych](../msbuild/media/distnode.png "DistNode")  
  
 Model rejestrowania rozproszonego rozszerza modelu centralnego rejestrowania przez umożliwienie tworzenia Rejestrator przekazujący.  
  
#### <a name="forwarding-loggers"></a>Przekazywanie rejestratorów  
 Rejestrator przekazujący jest rejestratora dodatkowej, lekkie, który ma filtr zdarzeń, które dołącza do węzła pomocniczego i odbiera zdarzenia przychodzące kompilacji z tego węzła. Filtruje zdarzenia przychodzące, a przekazuje tylko te, które określisz do centralnej węzła. Pozwala to ograniczyć ruch komunikat, który jest wysyłany do węzła centralnej i zwiększa ogólną wydajność kompilacji.  
  
 Istnieją dwa sposoby rejestrowanie rozproszonych, w następujący sposób:  
  
-   Dostosowywanie Rejestrator przekazujący wstępnie metalowych, o nazwie <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
-   Napisać własny Rejestrator przekazujący niestandardowych.  
  
 Można zmodyfikować ConfigurableForwardingLogger ze swoimi potrzebami. Aby to zrobić, zadzwoń rejestratora w wierszu polecenia, przy użyciu narzędzia MSBuild.exe, a listy zdarzeń kompilacji, które należy rejestratora do przesyłania dalej do centralnej węzła.  
  
 Alternatywnie można utworzyć Rejestrator przekazujący niestandardowych. Tworząc Rejestrator przekazujący niestandardowych, można dostosować zachowanie programu rejestrującego. Tworzenie Rejestrator przekazujący niestandardowy jest jednak bardziej skomplikowane niż właśnie dostosowywaniu ConfigurableForwardingLogger. Aby uzyskać więcej informacji, zobacz [tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Przy użyciu ConfigurableForwardingLogger prosty rozproszonych rejestrowania  
 Aby dołączyć ConfigurableForwardingLogger lub Rejestrator przekazujący niestandardowe, należy użyć `/distributedlogger` przełącznika (`/dl` skrócie) w MSBuild.exe kompilacji wiersza polecenia. Format służący do określania nazwy klas i typów rejestratora jest taka sama, jak dla `/logger` przełącznika, z wyjątkiem tego, czy rozproszonej rejestratora zawsze ma dwie klasy rejestrowania zamiast jeden rejestrator przekazujący i centralnego rejestrowania. Poniżej przedstawiono przykładowy sposób dołączania Rejestrator przekazujący niestandardowy o nazwie XMLForwardingLogger.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  Znak gwiazdki (*) muszą być rozdzielone rejestratora dwóch nazw w `/dl` przełącznika.  
  
 Przy użyciu ConfigurableForwardingLogger przypomina przy użyciu innych rejestratora (zgodnie z opisem w [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)), ale dołączyć rejestratora ConfigurableForwardingLogger zamiast typowe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestratora i Określ jako parametry zdarzeń, które chcesz ConfigurableForwardingLogger do przekazania do centralnej węzła.  
  
 Na przykład, jeśli chcesz otrzymywać powiadomienia tylko wtedy, gdy kompilacja początek i koniec i po wystąpieniu błędu, przejdzie `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, i `ERROREVENT` jako parametry. Wiele parametrów mogą być przekazywane, oddzielając je średnikami. Poniżej przedstawiono przykład sposobu użycia ConfigurableForwardingLogger do przekazywania tylko `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, i `ERROREVENT` zdarzenia.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Poniżej przedstawiono listę dostępnych parametrów ConfigurableForwardingLogger.  
  
|Parametry ConfigurableForwardingLogger|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|WIERSZ POLECENIA|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)