---
title: Zarządzanie wymagań dotyczących pakietu za pomocą pliku requirements.txt | Dokumentacja firmy Microsoft
description: Plik requirements.txt służy do zarządzania zależności projektu. Jeśli pojawi się projekt, który zawiera plik requirements.txt, można łatwo zainstalować tych zależności w jednym kroku.
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: b9d1a35d8ba34561c56ca14261591c7b80bacdb0
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="managing-required-packages-with-requirementstxt"></a>Zarządzanie wymagane pakiety z pliku requirements.txt

Współużytkuje projektem, przy użyciu systemu kompilacji, czy jest planowane [opublikowania go w usłudze Microsoft Azure](python-azure-cloud-service-project-template.md), należy określić pakiety zewnętrzne, które wymaga projektu. Zalecanym rozwiązaniem jest użycie [pliku requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) zawierający listę poleceń dla narzędzia pip, który instaluje wymagane wersje pakietów zależnych.

Z technicznego punktu widzenia nazwy pliku może służyć do śledzenia wymagania (przy użyciu `-r <full path to file>` podczas instalowania pakietu), ale Visual Studio zapewnia obsługę określonych `requirements.txt`:

- Jeśli został załadowany projekt, który zawiera `requirements.txt` i chcesz, aby zainstalować te pakiety wymienione w tym pliku, rozwiń węzeł **środowiska Python** w węźle **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy a następnie wybierz węzeł środowiska **Zainstaluj z pliku requirements.txt**:

    ![Zainstaluj z pliku requirements.txt](media/environments-requirements-txt-install.png)

- Jeśli masz już wszystkie niezbędne pakiety zainstalowane w środowisku, należy kliknąć prawym przyciskiem myszy tego środowiska w Eksploratorze rozwiązań i wybrać **Generuj plik requirements.txt** można utworzyć niezbędnego pliku. Jeśli plik już istnieje, zostanie wyświetlony monit o jak go zaktualizować:

    ![Opcje pliku requirements.txt aktualizacji](media/environments-requirements-txt-replace.png)

  - **Zastąp cały plik** usuwa wszystkie elementy, komentarze i opcje, które istnieją.
  - **Odśwież istniejących** wykrywa wymagań dotyczących pakietu i aktualizuje specyfikatory wersji, aby dopasować aktualnie zainstalowaną wersję.
  - **Aktualizowanie i dodawanie wpisów** odświeża wszelkie wymagania, które zostały znalezione i dodaje wszystkie inne pakiety na końcu pliku.

Ponieważ `requirements.txt` pliki mają zawiesza wymagania środowiska, wszystkie zainstalowane pakiety są zapisywane z użyciem wersji dokładne. Użycie wersji dokładne gwarantuje, że można łatwo odtworzyć środowiska na innym komputerze. Pakiety są dołączane, nawet jeśli zostały one zainstalowane z zakresem wersji, jako zależność inny pakiet, lub z Instalatorem niż pip.

Jeśli nie można zainstalować pakietu przez narzędzie pip, ale pojawia się `requirements.txt` niepowodzenia instalacji całego pliku. W takim przypadku ręcznie edytować plik, aby wykluczyć ten pakiet lub użyć [opcje przez narzędzie pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) do odwoływania się do zainstalowania wersji pakietu. Na przykład użytkownik może chcieć użyć [ `pip wheel` ](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) skompilować zależności, a następnie dodaj `--find-links <path>` opcji do Twojej `requirements.txt`:

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

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)