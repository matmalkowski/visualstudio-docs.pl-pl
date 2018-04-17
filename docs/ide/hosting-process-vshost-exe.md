---
title: Proces hostingu (vshost.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f11bed43a9595a3ce0034555f05a18f7a9dfa7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="hosting-process-vshostexe"></a>Proces hostingu (vshost.exe)
Proces hostingu jest funkcją w programie Visual Studio, która zwiększa wydajność debugowania, włącza debugowanie częściowej relacji zaufania i umożliwia obliczenie wyrażenia czasu projektowania. Pliki procesu hostingu zawierają *vshost* w pliku nazwa i są umieszczane w folderze wyjściowym projektu. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Hosting pliki procesów (*. vshost.exe*) służą do użytku przez program Visual Studio i nie należy uruchamiać bezpośrednio lub wdrożony z aplikacją.  
  
## <a name="improved-debugging-performance"></a>Zwiększono wydajność debugowania  
 Proces hostingu tworzy domeny aplikacji i kojarzy debugera z aplikacją. Wykonywania tych zadań mogą powodować zauważalne opóźnienia między debugowanie w czasie została uruchomiona i czas aplikacji uruchamia. Proces hostingu pomaga zwiększyć wydajność tworzenia domeny aplikacji i kojarzenie debugera w tle i zapisując domeny aplikacji i stanu debugera między uruchamia aplikacji. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
## <a name="partial-trust-debugging"></a>Debugowanie w częściowej relacji zaufania  
 Aplikację można określić jako aplikacja w częściowej relacji zaufania [Strona zabezpieczeń](../ide/reference/security-page-project-designer.md) z **projektanta projektu**. Debugowanie częściowo zaufanych aplikacji wymaga specjalnych inicjowania domeny aplikacji. Inicjowanie ten jest obsługiwany przez proces hostingu.  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Obliczanie wyrażenia czasu projektowania umożliwia testowanie kodu z **Immediate** okna bez konieczności uruchamiania aplikacji. Proces hostingu wykonuje ten kod podczas obliczania wyrażenia czasu projektowania. Aby uzyskać więcej informacji, zobacz [oknie bezpośrednim](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
 [Porady: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Domeny aplikacji](/dotnet/framework/app-domains/application-domains)