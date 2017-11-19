---
title: "Porady: Konfigurowanie projektów do wielu platform docelowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f862319d29502f1e3e242990072fbe0d2410fab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Porady: konfigurowanie projektów do wielu platform docelowych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]umożliwia rozwiązanie docelowy kilku różnych architektury Procesora lub platformy, na raz. Aby ustawić te właściwości są dostępne za pośrednictwem **programu Configuration Manager** okno dialogowe.  
  
## <a name="targeting-a-platform"></a>Przeznaczonych dla platformy  
 **Programu Configuration Manager** okno dialogowe umożliwia tworzenie i ustawianie konfiguracji rozwiązania i na poziomie projektu i platform. Każda kombinacja rozwiązanie na poziomie konfiguracji i elementy docelowe może mieć unikatowego zestawu właściwości skojarzone z nim, dzięki czemu można łatwo przełączać, na przykład konfiguracji wydanie którego element docelowy [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platformy, konfiguracja wydania które elementy docelowe x86 platformy i konfiguracji debugowania, którego celem jest x86 platformy.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Aby ustawić konfigurację, aby skorzystać z innej platformy  
  
1.  Na **kompilacji** menu, kliknij przycisk **programu Configuration Manager**.  
  
2.  W **aktywne rozwiązanie platformy pole**, wybierz platformę rozwiązania do obiektu docelowego, lub wybierz  **\<nowy >** do utworzenia nowej platformie. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zostanie skompilowany aplikacji pod kątem platformy, który jest ustawiony jako aktywnej platformy w **programu Configuration Manager** okno dialogowe.  
  
## <a name="removing-a-platform"></a>Trwa usuwanie platformy  
 Gdy uznasz, że użytkownik nie ma potrzeby dla platformy, należy usunąć go za pomocą okna dialogowego programu Configuration Manager. Spowoduje to usunięcie wszystkich ustawień rozwiązań i projektów, które skonfigurowane dla tej kombinacji konfiguracji i docelowej.  
  
#### <a name="to-remove-a-platform"></a>Aby usunąć platformy  
  
1.  Na **kompilacji** menu, kliknij przycisk **programu Configuration Manager**.  
  
2.  W **aktywne rozwiązanie platformy pole**, wybierz pozycję  **\<Edytuj >**. **Edytuj platformy rozwiązania** zostanie otwarte okno dialogowe.  
  
3.  Kliknij platformy, którą chcesz usunąć, a następnie kliknij przycisk **Usuń**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Przeznaczenie do wielu platform z jednym z rozwiązań  
 Nie można zmienić ustawienia, oparty na kombinacji konfiguracji i ustawień platformy, można skonfigurować rozwiązania, który może współpracować z więcej niż jedną platformę.  
  
#### <a name="to-target-multiple-platforms"></a>Do wielu platform docelowych  
  
1.  Użyj **programu Configuration Manager** można dodać co najmniej dwóch docelowych platform dla rozwiązania.  
  
2.  Wybierz platformę docelową z **platformy aktywne rozwiązanie** listy.  
  
3.  Skompiluj rozwiązanie.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Aby jednocześnie kompilowanie wielu konfiguracji rozwiązania  
  
1.  Użyj **programu Configuration Manager** można dodać co najmniej dwóch docelowych platform dla rozwiązania.  
  
2.  Użyj **tworzenia partii** okno, aby utworzyć jednocześnie kilka konfiguracji rozwiązania.  
  
 Istnieje możliwość ma ustawioną na przykład platforma rozwiązania na poziomie [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], i mieć żadnych projektów w ramach tego rozwiązania, korzystających z tej samej platformy. Jest również możliwe wielu projektów w rozwiązaniu każdego wybieranie różnych platform. Zaleca się, że w przypadku jednej z tych sytuacji, Utwórz nową konfigurację z opisową nazwę, aby uniknąć pomyłek.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)   
 [Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)