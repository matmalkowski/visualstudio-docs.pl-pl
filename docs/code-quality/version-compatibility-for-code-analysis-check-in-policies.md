---
title: Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25e8ee0bf46840d420f5537a2ca28965522dea43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
Jeśli należy ocenić i tworzyć przy użyciu różnych wersji zasad zaewidencjonowania dla analizy kodu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], musisz znać różnice w sposób [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] i [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] oceny zasad ewidencjonowania.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatybilność wersji dla oceny zasad ewidencjonowania

-   Gdy zasad ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], reguł, które były dostępne w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , ale nie istnieją w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] są ignorowane.

-   Gdy zasad ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], wszystkich nowych zasad, które są na wyłączność dla [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] są ignorowane.

-   Jeśli zasady analizy kodu zaewidencjonowania Określa zestawy reguł [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoruje wszystkie reguły, które są określone przez zestawy nie rozpoznaje.

-   Jeśli zasady analizy kodu zaewidencjonowania Określa zestawy reguł który [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie może rozpoznać, zostanie wyświetlony komunikat.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatybilność wersji dla tworzenia zasady ewidencjonowania

-   Jeśli zasad analizy kodu zaewidencjonowania utworzone przy użyciu [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] wersji [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], nie można użyć [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] wersji [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] do jej modyfikowania. A także [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie może oszacować zasady.

-   Jeśli utworzono zasad analizy kodu zaewidencjonowania przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], można użyć [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] do zmodyfikowania, a zasady mogą również oceniane przez [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Po zmodyfikowaniu zasad przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nie będzie można edytować zasady za pomocą [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] może służyć do oceny zasad bez problemów z niezgodnymi silnej nazwy.

-   Aby utworzyć zasad analizy kodu zaewidencjonowania za pomocą ustawień reguły, które są stosowane dla obu [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] i [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], należy utworzyć zasady w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], wprowadź wszystkie wymagane zmiany i zapisać zasady. Jeśli zmiany reguły istnieje tylko w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], zmodyfikuj i zapisz ją w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

     Po zapisaniu zasad w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nie będzie można zmienić ustawienia zasad, które istnieją w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] tylko.