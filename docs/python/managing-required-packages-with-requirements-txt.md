---
title: Zarządzanie wymagań dotyczących pakietu przy użyciu pliku requirements.txt
description: Zarządzanie zależnościami projektu, można użyć pliku requirements.txt. Jeśli zostanie wyświetlony projektu, który zawiera plik requirements.txt, możesz łatwo zainstalować te zależności w jednym kroku.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 478cb56856a5177f74b92542afadb0c36ac946c2
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548794"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Zarządzanie wymagane pakiety przy użyciu pliku requirements.txt

W przypadku udostępniania projektu z innymi osobami, za pomocą systemu kompilacji, czy planujesz [opublikowania go w usłudze Microsoft Azure](python-azure-cloud-service-project-template.md), należy określić zewnętrznych pakietów, których wymaga projekt. Zalecanym podejściem jest użycie [pliku requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) zawierający listę poleceń dla narzędzia pip, który instaluje wymagane wersje pakietów zależnych.

Technicznie rzecz biorąc, nazwy pliku może służyć do śledzenia wymagań (przy użyciu `-r <full path to file>` podczas instalowania pakietu), ale Visual Studio zapewnia obsługi *requirements.txt*:

- Jeśli został załadowany projekt, który zawiera *requirements.txt* i chcesz, aby zainstalować te pakiety wymienione w tym pliku, rozwiń węzeł **środowiska Python** w węźle **Eksploratora rozwiązań**, a następnie kliknij prawym przyciskiem myszy węzeł środowiska i wybierz **Zainstaluj z pliku requirements.txt**:

    ![Zainstaluj z pliku requirements.txt](media/environments-requirements-txt-install.png)

- Jeśli masz już niezbędne pakiety zainstalowane w środowisku, należy kliknąć prawym przyciskiem myszy tego środowiska w **Eksploratora rozwiązań** i wybierz **Generovat requirements.txt** do utworzenia niezbędnych plik. Jeśli plik już istnieje, zostanie wyświetlony monit dotyczące konieczność jej zaktualizowania:

    ![Opcje pliku requirements.txt aktualizacji](media/environments-requirements-txt-replace.png)

  - **Zastąp cały plik** usuwa wszystkie elementy, komentarze i opcje, które istnieją.
  - **Odśwież istniejące wpisy** wykrywa wymagań dotyczących pakietu i aktualizuje specyfikatory wersji, aby dopasować obecnie zainstalowaną wersję.
  - **Aktualizowanie i dodawanie wpisów** odświeża wszelkie wymagania, które znajdują się i dodaje wszystkie inne pakiety na końcu pliku.

Ponieważ *requirements.txt* pliki mają na celu Zablokuj wymagania środowiska, wszystkie zainstalowane pakiety są zapisywane z użyciem wersje dokładny. Użycie wersje dokładny gwarantuje, że łatwo można odtworzyć środowiska na innym komputerze. Pakiety są dołączane, nawet jeśli były zainstalowane z zakresem wersji, jako zależność z innym pakietem lub z Instalatorem niż pip.

Jeśli nie można zainstalować pakietu przez narzędzie pip i wyświetlone w *requirements.txt* pliku całej instalacji zakończy się niepowodzeniem. W takim przypadku ręcznie edytować plik, aby wykluczyć ten pakiet lub użyć [opcje firmy pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) do odwoływania się do instalowalną wersję pakietu. Na przykład użytkownik może chcieć użyć [ `pip wheel` ](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) skompilować zależności i dodać `--find-links <path>` opcję swoje *requirements.txt*:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

### <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Dokumentacja okna środowiska Python](python-environments-window-tab-reference.md)
