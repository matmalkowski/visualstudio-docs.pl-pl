---
title: Proces hostingu (vshost.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f33a5650230eced6f6713e943daba1ef0cacb74a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="hosting-process-vshostexe"></a>Proces hostingu (vshost.exe)
Proces hostingu jest funkcją w programie Visual Studio, która zwiększa wydajność debugowania, włącza debugowanie częściowej relacji zaufania i umożliwia obliczenie wyrażenia czasu projektowania. Pliki procesu hostingu zawierają vshost w nazwie pliku i są umieszczane w folderze wyjściowym projektu. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Hosting pliki procesów (. vshost.exe) służą do użytku przez program Visual Studio i nie należy uruchamiać bezpośrednio lub wdrożony z aplikacją.  
  
## <a name="improved-debugging-performance"></a>Zwiększono wydajność debugowania  
 Proces hostingu tworzy domeny aplikacji i kojarzy debugera z aplikacją. Wykonywania tych zadań mogą powodować zauważalne opóźnienia między debugowanie w czasie została uruchomiona i czas aplikacji uruchamia. Proces hostingu pomaga zwiększyć wydajność tworzenia domeny aplikacji i kojarzenie debugera w tle i zapisując domeny aplikacji i stanu debugera między uruchamia aplikacji. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
## <a name="partial-trust-debugging"></a>Debugowanie w częściowej relacji zaufania  
 Aplikację można określić jako aplikacja w częściowej relacji zaufania [Strona zabezpieczeń](../ide/reference/security-page-project-designer.md) z **projektanta projektu**. Debugowanie częściowo zaufanych aplikacji wymaga specjalnych inicjowania domeny aplikacji. Inicjowanie ten jest obsługiwany przez proces hostingu.  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Obliczanie wyrażenia czasu projektowania umożliwia testowanie kodu z **Immediate** okna bez konieczności uruchamiania aplikacji. Proces hostingu wykonuje ten kod podczas obliczania wyrażenia czasu projektowania. Aby uzyskać więcej informacji, zobacz [oknie bezpośrednim](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
 [Porady: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)