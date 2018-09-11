---
ms.technology: vs-ai-tools
ms.openlocfilehash: b7c8de18ba0083d31287fe862ab0015cb210bce1
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279638"
---
# <a name="view-recent-job-performance-and-details"></a>Wyświetl ostatnią wydajność zadania i szczegóły
Po przesłaniu zadania można wyświetlić listę zadań, aby wyświetlić ich stan, czas trwania i nie tylko.

1. W **Eksploratora serwera**, rozwiń węzeł kontekstu obliczeniowego określone.
1. Kliknij dwukrotnie **zadań**.
1. Zobaczysz listę zadania przesłane do danego kontekstu obliczeniowego.
1. Wybierz konkretną **zadania** na liście, aby wyświetlić szczegóły.

![Monitorowanie zadań](media\job-details\monitor-jobs.png)

> Historia zadania przesłane do maszyn wirtualnych systemu Linux są przechowywane na maszynie Wirtualnej w folderze/tmp katalogu. W związku z tym w każdym przypadku, gdy zostanie ona ponownie uruchomiona w historii zadań jest wyczyszczone. Stałe rekordu historii zadania skonfigurować swoją maszynę Wirtualną jako kontekst obliczeniowy w Azure Machine learning, następnie prześlij zadanie usługi Azure Machine Learning (Wybieranie maszyny Wirtualnej jako kontekst obliczeniowy).