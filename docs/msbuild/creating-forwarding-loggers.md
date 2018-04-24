---
title: Tworzenie przekazywania rejestratorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b95b0725e0cbb3a7568e51298fb83f05b74f18fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="creating-forwarding-loggers"></a>Tworzenie przekazywania rejestratorów
Przekazywanie rejestratorów poprawy efektywności rejestrowania, umożliwiając wybranie zdarzenia, które chcesz monitorować podczas kompilacji projektów w systemie wieloprocesorowym. Przez włączenie przekazywania rejestratorów, można zapobiec niechciane zdarzenia z przeciążając uda się rozpoznać rejestratora centralnego, spowalniając czas kompilacji i przeładowania dziennika.  
  
 Aby utworzyć Rejestrator przekazujący, możesz albo zaimplementuj <xref:Microsoft.Build.Framework.IForwardingLogger> interfejs, a następnie ręcznie zaimplementować metody lub użyj <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy i metody jego wstępnie skonfigurowane. (Te ostatnie będą wystarczające dla większości aplikacji.)  
  
## <a name="register-events-and-respond-to-them"></a>Rejestrowanie zdarzeń i odpowiadać na ich  
 Rejestrator przekazujący zbiera informacje o zdarzeniach kompilacji zgłoszonej przez aparat dodatkowej kompilacji, który jest tworzony przez proces kompilacji głównego podczas kompilacji w systemie wieloprocesorowym proces roboczy. Następnie Rejestrator przekazujący wybiera zdarzenia do przekazywania do rejestratora centralnego, na podstawie instrukcji nadany go.  
  
 Należy zarejestrować przekazywania rejestratorów do obsługi zdarzeń, które chcesz monitorować. Aby zarejestrować dla zdarzenia, należy zastąpić rejestratorów <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metody. Ta metoda obejmuje teraz opcjonalny parametr `nodecount`, które można ustawić liczby procesorów w systemie. (Domyślna wartość to 1).  
  
 Przykłady zdarzeń można monitorować <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 W środowisku wielu procesorów do odebrania poza kolejnością prawdopodobnie komunikaty o zdarzeniach. W związku z tym należy ocenić zdarzenia za pomocą programu obsługi zdarzeń w rejestrator przekazujący i program w celu sprawdzenia, jakie zdarzenia do przekazania do przekierowania do przekazywania danych do centralnej rejestratora. W tym celu można użyć <xref:Microsoft.Build.Framework.BuildEventContext> klasy, która jest dołączona do każdej wiadomości, aby ułatwić identyfikację zdarzenia, które mają być przekazywane, a następnie przekazać nazwy zdarzenia, które <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy (lub jej podklasy). Korzystając z tej metody, nie inne określonego kodowania jest wymagany do przekazywania zdarzenia.  
  
## <a name="specify-a-forwarding-logger"></a>Określ Rejestrator przekazujący  
 Po Rejestrator przekazujący został skompilowany w zestawie, należy wskazać [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do użycia go podczas kompilacji. Aby to zrobić, użyj `/FileLogger`, `/FileLoggerParameters`, i `/DistributedFileLogger` przełączniki wraz z MSBuild.exe. `/FileLogger` Przełącznika informuje MSBuild.exe czy rejestrator jest podłączony bezpośrednio. `/DistributedFileLogger` Przełącznika oznacza, że jest plik dziennika na każdy węzeł. Aby ustawić parametry Rejestrator przekazujący, użyj `/FileLoggerParameters` przełącznika. Aby uzyskać więcej informacji na temat tych i innych przełączników MSBuild.exe, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Kilku-procesorów obsługujących rejestratorów  
 W przypadku kompilowania projektu w systemie wieloprocesorowym wiadomości kompilacji z każdego procesora nie są automatycznie przeplotu ujednoliconego sekwencji. Zamiast tego należy ustanowić wiadomości grupujące priorytet przy użyciu <xref:Microsoft.Build.Framework.BuildEventContext> klasy, która jest dołączona do każdej wiadomości. Aby uzyskać więcej informacji dotyczących tworzenia wielu procesorów, zobacz [rejestrowania w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)