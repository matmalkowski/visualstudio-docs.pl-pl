---
title: '&lt;punkt wejścia&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 05e8e08718d9a0a87a1a3903e512c690ab0ebff8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689095"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;punkt wejścia&gt; — Element (aplikacja ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ &lt;punktu wejścia&gt; — Element (aplikacja ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/entrypoint-element-clickonce-application).  
  
Określa zestaw, który ma być wykonywane, kiedy to [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja jest uruchamiana na komputerze klienckim.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `entryPoint` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v2` przestrzeni nazw. Może istnieć tylko jeden `entryPoint` elementu zdefiniowanego w manifeście aplikacji.  
  
 `entryPoint` Element ma atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Opcjonalna. Ta wartość nie jest używana przez program .NET Framework.|  
  
 `entryPoint` zawiera następujące elementy.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Wymagane. Rola `assemblyIdentity` i jego atrybuty jest zdefiniowany w [ \<assemblyIdentity > Element](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture` Atrybutu tego elementu i `processorArchitecture` atrybutowi określonemu w `assemblyIdentity` innych miejscach w aplikacji manifestu musi być zgodny.  
  
## <a name="commandline"></a>Wiersz polecenia  
 Wymagane. Musi być obiektem podrzędnym obiektu `entryPoint` elementu. Go nie ma elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`file`|Wymagane. Lokalnego odwołania do zestawu startowego dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. Ta wartość nie może zawierać ukośnika (/) ani ukośnika odwrotnego (\\) separatorami ścieżki.|  
|`parameters`|Wymagane. Opisuje akcję wykonywaną z punktem wejścia. Jedyna prawidłowa wartość to `run`; Jeśli zostanie podany ciąg pusty, `run` zakłada, że.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Opcjonalna. Jeśli włączone, określa, że to wdrożenie zawiera składnik, który zostanie wdrożony wewnątrz niestandardowego hosta, a nie jest autonomiczną aplikacją.  
  
 Jeśli ten element jest obecny, `assemblyIdentity` i `commandLine` elementy nie również musi być obecny. Jeśli są one [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zgłosi błąd sprawdzania poprawności podczas instalacji.  
  
 Ten element ma żadnych atrybutów i żadne elementy podrzędne.  
  
## <a name="customux"></a>customUX  
 Opcjonalna. Określa, że aplikacja jest zainstalowana i obsługiwanego przez instalatora niestandardowego i nie utworzyć wpis menu Start, skrótu lub Dodaj lub usuń wpis programów.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Aplikacja, która zawiera customUX element należy podać niestandardowego Instalatora, które używa <xref:System.Deployment.Application.InPlaceHostingManager> klasy w celu wykonania instalacji operacji. Nie można zainstalować aplikacji przy użyciu tego elementu przez dwukrotne kliknięcie jej manifestu lub setup.exe wymagań wstępnych programu inicjującego. Można utworzyć niestandardowego Instalatora, elementy menu Start, skróty i wpisy apletu Dodaj lub usuń programy. Jeśli niestandardowego Instalatora nie powoduje utworzenia wpisu Dodaj lub usuń programy, identyfikator subskrypcji, dostarczone przez musi zostać zapisana <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> właściwość i umożliwiają użytkownikowi Odinstaluj tę aplikację później, przez wywołanie metody <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metody. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa zestaw i punktu wejścia dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
 Nie można użyć `commandLine` do przekazania parametrów do aplikacji w czasie wykonywania. Dostępne parametry ciągu zapytania dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia z poziomu aplikacji <xref:System.AppDomain>. Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `entryPoint` elementu w manifeście aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) tematu.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)



