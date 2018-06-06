---
title: 'Porady: uwzględnianie pliku danych w aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced10a16bae0e5892fddec1a79b9f7793b4dac43
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815548"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Porady: uwzględnianie pliku danych w aplikacji ClickOnce
Każdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalowania aplikacji jest przypisany katalog danych na dysku lokalnym komputera docelowego, której aplikacji można zarządzać własnych danych. Pliki danych może zawierać plików dowolnego typu: pliki tekstowe, pliki XML lub nawet pliki bazy danych (.mdb) programu Microsoft Access. Poniższe procedury pokazują, jak można dodać plik danych dowolnego typu do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Aby dołączyć plik danych przy użyciu Mage.exe  
  
1.  Dodawanie pliku danych do katalogu aplikacji z resztą pliki aplikacji.  
  
     Zazwyczaj katalogu aplikacji jest katalogiem etykietą wdrożenia bieżącej wersji — na przykład v1.0.0.0.  
  
2.  Zaktualizuj manifest aplikacji do listy plików danych.  
  
     `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
     Wykonanie tego zadania ponownie utworzy listę plików w manifeście aplikacji i automatycznie generuje podpisów wyznaczania wartości skrótu.  
  
3.  Otwórz plik manifestu aplikacji w preferowanym tekstu lub edytora XML i Znajdź `file` element ostatnio dodany plik.  
  
     Jeśli dodano plik XML o nazwie `Data.xml`, plik będzie wyglądała podobnie do poniższego przykładu kodu.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Dodaj atrybut `type` do tego elementu i przekazać jej wartość `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Ponownie podpisać manifest aplikacji przy użyciu pary kluczy lub certyfikatu, a następnie ponownie zaloguj manifeście wdrażania.  
  
     Musi ponownie podpisać manifeście wdrażania, ponieważ jego skrót manifest aplikacji została zmieniona.  
  
     `mage -s app manifest -cf cert_file -pwd password`
  
     `mage -u deployment manifest -appm app manifest`
  
     `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Aby dołączyć plik danych przy użyciu MageUI.exe  
  
1.  Dodawanie pliku danych do katalogu aplikacji z resztą pliki aplikacji.  
  
2.  Zazwyczaj katalogu aplikacji jest katalogiem etykietą wdrożenia bieżącej wersji — na przykład v1.0.0.0.  
  
3.  Na **pliku** menu, kliknij przycisk **Otwórz** otworzyć manifest aplikacji.  
  
4.  Wybierz **pliki** kartę.  
  
5.  W polu tekstowym u góry karty wprowadź katalog zawierający pliki aplikacji, a następnie kliknij przycisk **wypełnij**.  
  
     Plik danych będą wyświetlane w siatce.  
  
6.  Ustaw **typ pliku** wartości w pliku danych do **danych**.  
  
7.  Zapisz manifest aplikacji, a następnie ponownie podpisać plik.  
  
     MageUI.exe wyświetli monit o ponowne podpisanie pliku.  
  
8.  Ponowne podpisanie manifeście wdrażania  
  
     Musi ponownie podpisać manifeście wdrażania, ponieważ jego skrót manifest aplikacji została zmieniona.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)