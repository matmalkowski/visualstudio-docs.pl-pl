---
title: Sprawdzanie poprawności ramek grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9732cd3f3440448e5096e71f838d8ebcf20fb13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473962"
---
# <a name="graphics-frame-validation"></a>Sprawdzanie poprawności ramek grafiki
<!-- VERSIONLESS -->
Visual Studio 2017 i lepsze wsparcie **weryfikacji ramki** narzędzia.  Okna ramowe sprawdzania wyświetla błędy i ostrzeżenia skojarzony z listy zdarzeń.  Aby wyświetlić to okno, wybierz **Widok > Ramka weryfikacji** menu.

![Sprawdzanie poprawności ramki](media/gfx_diag_frame_validation.png)

Kliknij przycisk **Uruchom weryfikację** przycisk w lewym górnym rogu, aby zainicjować analizy.  Może upłynąć kilka minut w zależności od złożoności ramki.  Danych, która pojawia się tutaj składa się z dwóch źródeł: komunikaty D3D tego samego emituje podczas [warstw zestawu SDK](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx) jest włączona i dane, które mają być zbierane z stan wewnętrzny własne narzędzia śledzenia. Po zakończeniu zostanie wyświetlony kilka kolumn danych:

**Kolumny**|**Opis**
---|---
Identyfikator zdarzenia | Identyfikator, który mapuje do zapisu w [listy zdarzeń](graphics-event-list.md) okna.
Ważność | Uszkodzenie, błąd, ostrzeżenie, informacje lub wiadomości.
Kategoria | Aplikacji określone, dodatkowe, inicjowania, oczyszczania, kompilacji, tworzenia stanu, ustawienie stanu, pobieranie stanu, wykonanie, manipulowanie zasobów i programu do cieniowania, nadmiarowe i nieużywanych.
Komunikat | Komunikat skojarzony ze zdarzeniem.
Zdarzenie | Zdarzenia związane z błąd lub ostrzeżenie.

## <a name="see-also"></a>Zobacz też  
[Diagnostyka grafiki (debugowania grafiki DirectX)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->