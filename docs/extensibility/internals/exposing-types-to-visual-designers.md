---
title: "Udostępnianie typów wizualnych projektantów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e79ec644426ed5068f79bb914b1202a800982cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-types-to-visual-designers"></a>Udostępnianie typów wizualnych projektantów
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]musi mieć dostęp do definicje klas i typów w czasie projektowania, aby wyświetlić wizualnego projektanta. Klasy są ładowane z wstępnie zdefiniowane zestawy, które obejmują pełne zależności zestawu bieżącego projektu (odniesienia oraz ich zależności). Może być również wymagany do dostępu do klas i typów, które są zdefiniowane w plikach wygenerowanych przez narzędzia niestandardowe wizualnych projektantów.  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systemów projektów zapewniają obsługę do uzyskiwania dostępu do wygenerowanych klas i typów za pośrednictwem tymczasowego przenośne pliki wykonywalne (PEs tymczasowe). Każdy plik generowane przez niestandardowe narzędzie można można skompilować do tymczasowego zestawu tak, aby typy mogą być ładowane z tych zestawów i widoczne dla projektantów. Dane wyjściowe narzędzia niestandardowego jest kompilowany do oddzielnych tymczasowych, a powodzenie lub niepowodzenie Ta kompilacja tymczasowego zależy tylko czy mogą być kompilowane wygenerowanego pliku. Nawet jeśli projekt nie może zbudować jako całość, poszczególnych PEs tymczasowego może nadal być dostępny dla projektantów.  
  
 System projektu zapewnia pełną obsługę śledzenia zmian do pliku dane wyjściowe narzędzia niestandardowego, pod warunkiem, że te zmiany są wynik uruchomienia narzędzia niestandardowego. Każdym uruchomieniu narzędzia niestandardowego jest generowany nowy tymczasowych i odpowiednie powiadomienia są wysyłane do projektantów.  
  
> [!NOTE]
>  Ponieważ plik wykonywalny Generowanie tymczasowego programu przebiega w tle, żadne błędy nie są zgłoszone dla użytkownika, jeśli kompilacja zakończy się niepowodzeniem.  
  
 Narzędzi niestandardowych, które wykorzystać zalety tymczasowe środowiska Preinstalacyjnego należy wykonać następujące reguły:  
  
-   `GeneratesDesignTimeSource`musi być równa 1 w rejestrze.  
  
     Kompilacja pliku wykonywalnego nie program nie działa bez tego ustawienia.  
  
-   Wygenerowany kod musi być w tym samym języku co ustawienie globalne projektu.  
  
     Tymczasowych jest kompilowany niezależnie od tego, narzędzie niestandardowe raporty, żądane rozszerzenie w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> pod warunkiem, że `GeneratesDesignTimeSource` jest ustawiona na 1 w rejestrze. Rozszerzenie musi być .vb, .cs lub .jsl; może to być wszystkie rozszerzenia.  
  
-   Kod wygenerowany przez niestandardowe narzędzie musi być prawidłowy, i należy go skompilować na jego własnej przy użyciu tylko zestawu odwołań w projekcie w czasie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> ukończeniem wykonywania.  
  
     Podczas kompilowania tymczasowych tylko plik źródłowy podany w kompilatorze jest dane wyjściowe narzędzia niestandardowego. W związku z tym niestandardowe narzędzie, które używa tymczasowych, należy wygenerować pliki wyjściowe, które mogą być kompilowane niezależnie od innych plików w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt BuildManager — wprowadzenie](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementowanie generatory pojedynczego pliku](../../extensibility/internals/implementing-single-file-generators.md)   
 [Rejestrowanie generatory pojedynczego pliku](../../extensibility/internals/registering-single-file-generators.md)