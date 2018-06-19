---
title: Rejestratory kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40ce48f8fc21c1c035586edf48446ce1d3f103d3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570463"
---
# <a name="build-loggers"></a>Rejestratory kompilacji
Rejestratory umożliwiają dostosowanie dane wyjściowe kompilacji i wyświetlić wiadomości, błędy lub ostrzeżenia w odpowiedzi na zdarzenia określonej kompilacji. Każdy rejestrator jest zaimplementowany jako klasy .NET, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs, który jest zdefiniowany w zestawie Microsoft.Build.Framework.dll.  
  
 Istnieją dwie metody, używanego podczas implementowania Rejestrator:  
  
-   Implementowanie <xref:Microsoft.Build.Framework.ILogger> interfejsu bezpośrednio.  
  
-   Klasy być pochodną klasy Pomocnika <xref:Microsoft.Build.Utilities.Logger>, który jest zdefiniowany w zestawie Microsoft.Build.Utilities.dll. <xref:Microsoft.Build.Utilities.Logger> implementuje <xref:Microsoft.Build.Framework.ILogger> i zawiera domyślne implementacje niektórych <xref:Microsoft.Build.Framework.ILogger> elementów członkowskich.  
  
 W tym temacie będzie wyjaśniono sposób pisania prostych rejestratora, która pochodzi z <xref:Microsoft.Build.Utilities.Logger>, i wyświetla komunikaty w konsoli w odpowiedzi na niektóre zdarzenia kompilacji.  
  
## <a name="registering-for-events"></a>Rejestracja nasłuchiwania zdarzeń  
 Rejestrator ma na celu zbierać informacje o postępie kompilacji zgłoszonej przez aparat kompilacji, a następnie składają raporty te informacje w przystępny sposób. Należy zastąpić wszystkie rejestratorów <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodę, która jest, gdzie rejestratora rejestruje zdarzeń. W tym przykładzie rejestruje rejestratora <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> zdarzenia.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>Odpowiadanie na zdarzenia  
 Teraz, gdy rejestratora jest zarejestrowany dla określonych zdarzeń, musi obsługiwać tych zdarzeń, jeśli występują. Aby uzyskać <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> zdarzenia, Rejestrator zapisuje po prostu krótka fraza i nazwa pliku projektu objętego zdarzeniem. Wszystkie komunikaty z Rejestratora są zapisywane w oknie konsoli.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Odpowiada wartości szczegółowości rejestratora  
 W niektórych przypadkach warto tylko rejestrowanie informacji z zdarzenia, jeśli programu MSBuild.exe **/verbosity** przełącznik zawiera określoną wartość. W tym przykładzie <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> obsługi zdarzeń tylko rejestruje komunikat, jeśli <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> właściwość, która jest ustawiana przez **/verbosity** przełącznika, jest równa <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>Określanie Rejestrator  
 Gdy rejestratora jest kompilowany do zestawu, należy przekazać do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do używania tego rejestratora podczas kompilacji. Jest to realizowane przy użyciu **/logger** przełącznik z MSBuild.exe. Aby uzyskać więcej informacji na temat parametrów, które są dostępne dla MSBuild.exe, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
 Następujące polecenie w wierszu kompilacji projektu `MyProject.csproj` i używa klasy rejestratora zaimplementowana w `SimpleLogger.dll`. **/Nologo** przełącznika ukrywa transparent i komunikat o prawach autorskich oraz **/noconsolelogger** przełącznik wyłącza domyślne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestratora konsoli.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Następujące polecenie w wierszu tworzy projekt o tej samej rejestratora, ale z `Verbosity` poziom `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kompletny kod dla rejestratora.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, jak do zaimplementowania rejestrowania, który zapisuje dziennik do pliku, a nie jej wyświetlania w oknie konsoli.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)