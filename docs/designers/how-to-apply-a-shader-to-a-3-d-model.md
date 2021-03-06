---
title: 'Porady: stosowanie cieniowania do modelu 3D'
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
ms.openlocfilehash: 12fc18532888dbf688c3fcc0e5695edfaf47d953
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924138"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Porady: stosowanie cieniowania do modelu 3D

W tym artykule przedstawiono sposób używania edytora modelu do zastosowania modułu cieniującego kierowane wykres modułu cieniującego języka (DGSL) do modelu 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Stosowanie cieniowania do modelu 3D

Efekt programu cieniującego można zastosować do modelu 3D w celu nadania mu interesującym wyglądem.

Przed rozpoczęciem upewnij się, że **właściwości** zostanie wyświetlone okno.

1. Rozpoczynają się od sceny 3D, który zawiera co najmniej jednego modelu. Jeśli nie masz odpowiedniego sceny 3D, utwórz ją zgodnie z opisem w [porady: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md). Musisz również posiadać modułu cieniującego DGSL, które można zastosować do modelu. Jeśli nie masz odpowiedniego programu do cieniowania, utwórz ją zgodnie z opisem w [porady: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że po zapisaniu go w pliku przed kontynuowaniem.

2. W **wybierz** tryb, wybierz model, do której ma dotyczyć programu do cieniowania, a następnie w **właściwości** okna w **Filename** właściwość **efektu**  właściwość konto należy do grupy określ modułu cieniującego DGSL, który chcesz zastosować do modelu.

Oto modelu, który ma zastosowano efekt kolor podstawowy:

![3&#45;scen D, które przedstawiono efekt koloru podstawowego](../designers/media/digit-3d-model-effect.png)

Po zastosowaniu cieniowania do modelu, możesz go otworzyć w projektancie programu do cieniowania, wybierając modelu, a następnie w **właściwości** okna w **(zaawansowane)** właściwość **efekt**grupy właściwości, wybierając wielokropek (**...** ) przycisku.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)