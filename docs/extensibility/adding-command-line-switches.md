---
title: "Dodawanie przełączniki wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e292a08e6d8ac9c6f59f84514fbb625779f82c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-command-line-switches"></a>Dodawanie przełączniki wiersza polecenia
Możesz dodać przełączniki wiersza polecenia, które dotyczą VSPackage, gdy jest wykonywana devenv.exe. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Aby zadeklarować nazwy przełącznika i jego właściwości. W tym przykładzie przełącznika MySwitch zostanie dodany do podklasy pakiet VSPackage o nazwie **AddCommandSwitchPackage** bez argumentów i VSPackage ładowane automatycznie.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 W poniższej tabeli przedstawiono parametry nazwane  
  
 Argumenty  
 Liczba argumentów dla przełącznika. Może być "*", lub listy argumentów.  
  
 DemandLoad  
 Automatycznie załadować pakiet VSPackage, jeśli ta jest równa 1, w przeciwnym razie wartość równa 0.  
  
 HelpString —  
 Pomocy ciąg lub zasobu o identyfikatorze ciągu do wyświetlenia z **devenv /?**.  
  
 Nazwa  
 Przełącznik.  
  
 PackageGuid  
 Identyfikator GUID pakietu.  
  
 Pierwsza wartość argumentów jest zwykle 0 lub 1. Specjalna wartość "*" może służyć do wskazywania argument całą pozostałą część wiersza polecenia. Może to być przydatne w przypadku debugowania scenariuszy, w którym użytkownik musi przejść w parametrach polecenia debugera.  
  
 Wartość DemandLoad to `true` (1) lub `false` (0) oznacza, że pakiet VSPackage powinny być ładowane automatycznie.  
  
 Wartość HelpString — jest identyfikator zasobu ciągu, która jest wyświetlana w devenv /? Wyświetlanie pomocy. Ta wartość powinna być w formie "#nnn" gdzie nnn jest liczbą całkowitą. Wartość ciągu w pliku zasobów powinien kończyć się znak nowego wiersza.  
  
 Wartość Nazwa jest nazwą przełącznika.  
  
 Wartość PackageGuid jest identyfikator GUID pakietu, który implementuje ten przełącznik. IDE używa tego identyfikatora GUID, aby znaleźć pakiet VSPackage w rejestrze, którego dotyczy przełącznik wiersza polecenia.  
  
## <a name="retrieving-command-line-switches"></a>Trwa pobieranie przełączniki wiersza polecenia  
 Podczas ładowania pakietu można pobrać przełączniki wiersza polecenia, wykonując następujące kroki.  
  
1.  W pakiecie VSPackage w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji, wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> uzyskanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfejsu.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> można pobrać przełączniki wiersza polecenia, które użytkownik wprowadził.  
  
 Poniższy kod przedstawia sposób dowiedzieć się, czy przełącznik wiersza polecenia MySwitch została wprowadzona przez użytkownika:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Jest obowiązek sprawdzaj przełączniki wiersza polecenia zawsze, gdy jest ładowany do pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Narzędzie elementu CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Plików Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)