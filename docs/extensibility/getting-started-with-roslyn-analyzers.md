---
title: Wprowadzenie do analizatorów Roslyn | Dokumentacja firmy Microsoft
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41db830fbf7dcbe97f44d64ffa9b9701ec658c1e
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370591"
---
# <a name="get-started-with-roslyn-analyzers"></a>Wprowadzenie do analizatorów Roslyn

Za pomocą analizatorów kodu na żywo, na podstawie projektu w programie Visual Studio autorzy interfejsu API może wysłać analizy kodu specyficznego dla domeny jako część pakietów NuGet. Ponieważ te analizatory są obsługiwane przez platformę kompilatora programu .NET (kodu "Roslyn"), mogą wygenerować ostrzeżeń w kodzie podczas wpisywania, nawet w przypadku, zanim zakończeniu wiersz (nie ma więcej oczekiwanie do kompilowania swojego kodu, aby wykryć problemy). Analizatory również może pojawiać się poprawki automatyczne kodu za pomocą programu Visual Studio żarówki po wyświetleniu monitu pozwalają na kod czyszczenia natychmiast.

## <a name="get-started"></a>Wprowadzenie

[Wprowadzenie do analizatorów kodu na żywo Roslyn i wskazówki](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Dodaj kod naprawia wskazówki: Podaj użytkowników poprawki analizator problemów](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Wprowadzenie i wskazówki dotyczące rzeczywistych analizatora](https://channel9.msdn.com/events/Build/2015/3-725)

[Analizator Roslyn rzeczywistych](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , możesz też obejrzeć jako [mówić](https://channel9.msdn.com/events/Build/2015/3-725)

[Kilka przykładów w witrynie github, pogrupowane według trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Wprowadzenie i przewodnik po kilku analizatorów](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Więcej dokumentów w witrynie github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reguł programu FxCop implementowane za pomocą analizatorów Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)