---
title: Dodawanie rozszerzeń do definicji DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7de01ec87ca4367dcd3453c41e38c653c5184beb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="add-extensions-to-dsl-definitions"></a>Dodawanie rozszerzenia do definicji DSL

Rozszerzenie definicji DSL pozwala utworzyć pakiet rozszerzenia języka specyficznego dla domeny (DSL). Rozszerzenie DSL, który jest zawarty w Visual Studio integracji rozszerzenia (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak DSL. Dodatkowe funkcje można dynamicznie włączone i wyłączone w czasie wykonywania. DSLs nie muszą być jawnie zaprojektowane dla rozszerzenia i rozszerzeń można zaprojektować później, lub przez osoby trzecie, bez zmiany rozszerzonej DSL.

Rozszerzenia DSL może obejmować następujące funkcje:

-   Właściwości modelu i elementy prezentacji

-   Elementy decorator dla łączników i kształtów

-   Klasy, relacje kształty i łączniki

-   Ograniczenia walidacji

-   Karty i elementy przybornika

Użytkownik DSL rozszerzonej mogą tworzyć i zapisywać modelu, który zawiera wystąpienia dodatkowe funkcje. Model może zostać odczytany przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowano rozszerzenia nie może używać dodatkowych funkcji, ale można zaktualizować i zapisywanie modelu bez utraty dodatkowe funkcje.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Wpisy na blogu pokrewne](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
