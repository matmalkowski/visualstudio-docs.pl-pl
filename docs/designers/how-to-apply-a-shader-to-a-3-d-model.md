---
title: 'Porady: zastosowanie programu do cieniowania do modelu 3D'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08e1a6b8bab7e6336f764f871328e0d56ad0c2f2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Porady: zastosowanie programu do cieniowania do modelu 3D

W tym artykule przedstawiono sposób użycia w edytorze modeli do zastosowania do cieniowania skierowane wykres programu do cieniowania języka (DGSL) do modelu 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Zastosowanie programu do cieniowania do modelu 3D

Efekt cieniowania można stosować do modelu 3D, aby nadać jej wygląd interesujące.

Przed rozpoczęciem upewnij się, że **właściwości** okno jest wyświetlane.

1. Zaczynać sceny 3W, która zawiera co najmniej jednego modelu. Jeśli nie masz odpowiedniego scenę 3D, utwórz go zgodnie z opisem w [porady: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md). Możesz również muszą mieć cieniowania DGSL, którą można zastosować do modelu. Jeśli nie masz odpowiedniego programu do cieniowania, utwórz go zgodnie z opisem w [porady: Tworzenie podstawowego cieniowania kolor](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że zapisane do pliku przed kontynuowaniem.

2. W **wybierz** tryb, wybierz model, który chcesz zastosować programu do cieniowania, a następnie w **właściwości** okna w **Filename** właściwość **efektu**  właściwości grupa, określ DGSL programu do cieniowania, który chcesz zastosować do modelu.

Oto modelu, który ma wpływ kolor podstawowy stosowane:

![3&#45;sceny D, pokazujący efekt kolor podstawowy](../designers/media/digit-3d-model-effect.png)

Po zainstalowaniu programu do cieniowania do modelu, można otworzyć go w projektancie programu do cieniowania, wybierając modelu, a następnie w **właściwości** okna w **(zaawansowane)** właściwość **efekt**grupy właściwości, wybierając wielokropek (**...** ) przycisku.

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)