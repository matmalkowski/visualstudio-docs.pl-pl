---
title: Dodawanie rozszerzenia do definicji DSL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a689d902a58eb747cbaec0bf7cebd740ade3e9bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji DSL
Rozszerzenie definicji DSL pozwala utworzyć pakiet rozszerzenia języka specyficznego dla domeny (DSL). Rozszerzenie DSL, który jest zawarty w Visual Studio integracji rozszerzenia (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak DSL. Dodatkowe funkcje można dynamicznie włączone i wyłączone w czasie wykonywania. DSLs nie muszą być jawnie zaprojektowane dla rozszerzenia, a rozszerzenia można zaprojektować później lub osobom trzecim bez zmiany rozszerzonej DSL.  
  
 Dodatkowe funkcje mogą być następujące:  
  
-   Właściwości modelu i elementy prezentacji  
  
-   Elementy decorator dla łączników i kształtów  
  
-   Klasy i relacje, kształtów łączników  
  
-   Ograniczenia walidacji  
  
-   Karty i elementy przybornika  
  
 Użytkownik rozszerzonej DSL można tworzyć i zapisywać modelu, który zawiera wystąpienia dodatkowe funkcje i mogą być odczytywane przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowano rozszerzenia nie może używać dodatkowych funkcji, ale można zaktualizować i zapisywanie modelu bez utraty dodatkowe funkcje.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też  
 [Wpisy na blogu pokrewne](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
