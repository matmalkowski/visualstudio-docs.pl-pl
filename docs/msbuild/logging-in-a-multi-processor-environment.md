---
title: Rejestrowanie w środowisku wielu procesorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dedf90c51ec2cd4f1864d5573925ed17a0d69b2a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31575381"
---
# <a name="logging-in-a-multi-processor-environment"></a>Logowanie w środowisku wielu procesorów
Możliwość używania wielu procesorów MSBuild może znacznie skrócić czas tworzenia projektu, ale również dodaje złożoność do rejestrowania. W środowisku z jednym procesorem rejestratora może obsługiwać przychodzące zdarzenia, wiadomości, ostrzeżenia i błędy w sposób przewidywalne, sekwencyjnych. Jednak w środowisku wielu procesorów z wielu źródeł można odebrania zdarzeń równocześnie lub poza kolejnością. MSBuild udostępnia nowe rejestratora kilku-procesorów obsługujących i umożliwia tworzenie niestandardowych "przekazywanie rejestratorów."  
  
## <a name="logging-multiple-processor-builds"></a>Rejestrowanie wielu procesorów kompilacje  
 Po utworzeniu co najmniej jeden projekt w systemie wieloprocesorowym lub wielordzeniowych zdarzenia MSBuild kompilacji dla wszystkich projektów, zostaną wygenerowane jednocześnie. Lawiny dane zdarzeń może pojawić się u rejestratora, w tym samym czasie lub poza kolejnością. To przeciąży rejestratora i spowodować razy większa kompilacji, Rejestrator nieprawidłowe dane wyjściowe lub uszkodzony kompilacji. Aby rozwiązać te problemy, rejestratora MSBuild można przetworzyć zdarzenia sekwencji i korelowanie zdarzeń i ich źródła.  
  
 Można zwiększyć wydajność rejestrowania jeszcze więcej tworząc Rejestrator przekazujący niestandardowych. Rejestrator przekazujący niestandardowe działa jako filtr można wybrać, przed utworzeniem, zdarzenia, który chcesz monitorować. Gdy używasz Rejestrator przekazujący niestandardowych niechciane zdarzenia nie przeciąży rejestratora, zajmowały dzienników lub wolno kompilacji razy.  
  
### <a name="central-logging-model"></a>Model centralnego rejestrowania  
 Dla kompilacji z wielu procesorów program MSBuild używa "model centralnego rejestrowania". W modelu centralnego rejestrowania wystąpienia MSBuild.exe działa jako proces kompilacji głównej lub "centralnej węzeł". Dodatkowej wystąpień MSBuild.exe lub "dodatkowej węzłów," są dołączone do centralnej węzła. Rejestratory na podstawie ILogger dołączony do węzła centralnej są określane jako "centralnej rejestratorów" i rejestratorów dołączony do węzłów dodatkowej są określane jako "dodatkowej rejestratorów."  
  
 Podczas kompilacji pomocniczej rejestratorów kierować ruchem ich zdarzeń do centralnej rejestratorów. Ponieważ zdarzenia generowane przez kilka węzłów dodatkowej, te dane dociera do lokalizacji centralnej węzła jednocześnie, ale przeplotu. Można rozpoznać odwołania do zdarzeń do projektu i cel zdarzenia, argumenty zdarzenia obejmują informacje o kontekście zdarzeń dodatkowe kompilacji.  
  
 Chociaż tylko <xref:Microsoft.Build.Framework.ILogger> jest wymagane do zaimplementowania przez centralną rejestratora, zalecamy również stosowanie <xref:Microsoft.Build.Framework.INodeLogger> Jeśli chcesz rejestratora centralnego zainicjować z liczbą węzłów, które uczestniczą w kompilacji. Następujące przeciążenia z <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metoda jest wywoływana, gdy aparat rejestratora:  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Model rejestrowania rozproszonego  
 W modelu centralnego rejestrowania zbyt dużej ilości ruchu przychodzącego komunikatu, takie jak podczas tworzenia wielu projektów jednocześnie, może spowodować przeciążenie centralnej węzła, który podkreśla systemu i obniża wydajność kompilacji.  
  
 Aby ograniczyć ten problem, MSBuild umożliwia także "modelu rozproszonych rejestrowania", rozszerzający modelu centralnego rejestrowania, umożliwiając tworzenie przekazywania rejestratorów. Rejestrator przekazujący jest dołączony do węzła pomocniczego i odbiera zdarzenia przychodzące kompilacji tego węzła. Rejestrator przekazujący działa tak jak zwykły rejestratora, z tą różnicą, że można filtrować zdarzenia, a następnie przesyła te żądany węzeł centralnej. Zmniejsza ruch komunikatów w węźle centralnej i w związku z tym zapewnia lepszą wydajność.  
  
 Rejestrator przekazujący można tworzyć z zastosowaniem <xref:Microsoft.Build.Framework.IForwardingLogger> interfejsu, która jest pochodną <xref:Microsoft.Build.Framework.ILogger>. Interfejs jest określony jako:  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Przekazywanie zdarzeń w rejestrator przekazujący, wywołaj <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> metody <xref:Microsoft.Build.Framework.IEventRedirector> interfejsu. Przekaż odpowiednie <xref:Microsoft.Build.Framework.BuildEventArgs>, lub pochodnej, jako parametr.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Dołączanie rozproszonej rejestratora  
 Aby dołączanie rozproszonej rejestratora kompilacji wiersza polecenia, użyj `/distributedlogger` (lub, `/dl` skrócie) przełącznika. Format służący do określania nazwy klas i typów rejestratora są takie same jak te dotyczące `/logger` przełącznika, z wyjątkiem tego rejestratora rozproszonej składa się z dwóch klas rejestrowania: Rejestrator przekazujący i centralnego rejestrowania. Poniżej przedstawiono przykład dołączanie rejestratora rozproszonych:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Znak gwiazdki (*) oddziela dwa rejestratora nazw w `/dl` przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)