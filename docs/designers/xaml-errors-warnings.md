---
title: XAML błędy i ostrzeżenia
ms.date: 03/06/2018
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b252fe651355000f63c47c5b45cf6d0e9db4d776
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="xaml-errors-and-warnings"></a>XAML błędy i ostrzeżenia

Podczas tworzenia pliku XAML, Visual Studio analizę kodu podczas pisania. Wężyk jest wyświetlany w wierszu kodu, gdy zostanie wykryty błąd. Ustawiając kursor nad wężyk zapewnia więcej informacji na temat błędu lub ostrzeżenia. Niektóre błędy i ostrzeżenia żarówka szybkiego działania zostanie wyświetlony, przy użyciu **Ctrl**+**.** skrót klawiaturowy Wyświetla opcje, aby rozwiązać ten problem.

## <a name="error-types"></a>Error — typy

W tle wielu narzędzi analizować XAML równolegle. Błędy XAML są podzielone na jeden z następujących trzech typów oparte na narzędzie wykryto błąd:

|**Wykrył błąd**|**Błąd formatu kodu**|
|--------------------------------|-----------------|
|Usługa języka XAML (edytora XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|XAML Edytuj i Kontynuuj|XECxxxx|

> [!Note]
> Nie wszystkie błędy lub ostrzeżenia mają odpowiedni kod. Takie błędy są zwykle błędy projektanta XAML.


## <a name="suppress-xaml-designer-errors"></a>Pomiń błędy projektanta XAML

Otwórz **opcje** okna dialogowego, wybierając **Narzędzia > Opcje**, a następnie wybierz **Edytor tekstu > XAML > różne**.

Usuń zaznaczenie pola wyboru **Pokaż błędy wykryte przez projektanta XAML** pole wyboru.

![Pomiń błędy projektanta XAML](../designers/media/suppress_xaml_designer_errors.PNG "SuppressXAMLDesignerErrors")


