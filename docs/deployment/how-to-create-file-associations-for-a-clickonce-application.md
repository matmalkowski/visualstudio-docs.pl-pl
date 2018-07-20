---
title: 'Porady: Tworzenie skojarzeń plików dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bcffae0cadfb5973b532fcca5b0356eba004762
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152698"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Porady: Tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje mogą być skojarzone z jednego lub więcej rozszerzeń nazw plików, więc, że aplikacja będzie uruchamiana automatycznie kiedy użytkownik otwiera plik z tych typów. Dodaniem obsługi rozszerzenia nazwy pliku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji jest bardzo proste.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce  
  
1.  Tworzenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zwykle, lub użyj istniejącej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
2.  Otwórz manifest aplikacji przy użyciu tekstu lub edytorze XML, takiego jak Notatnik.  
  
3.  Znajdź `assembly` elementu. Aby uzyskać więcej informacji, zobacz [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Jako element podrzędny elementu `assembly` elementu Dodawanie `fileAssociation` elementu. `fileAssociation` Element ma cztery atrybuty:  
  
    -   `extension`Rozszerzenie nazwy pliku, który chcesz skojarzyć z aplikacją.  
  
    -   `description`Opis typ pliku, który pojawi się w usłudze Windows shell.  
  
    -   `progid`: Ciąg unikatowo identyfikujący typ pliku, aby oznaczyć go w rejestrze.  
  
    -   `defaultIcon`: Ikony do użycia dla tego typu pliku. Ikony, należy dodać jako zasób w pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Na przykład `file` i `fileAssociation` elementów, zobacz [ \<fileassociation — > Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementów. Należy pamiętać, że `progid` atrybut powinien być inne dla każdego.  
  
6.  Po zakończeniu manifest aplikacji, należy ponownie podpisać manifest. Możesz to zrobić z wiersza polecenia, za pomocą *Mage.exe*.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Zobacz także  
 [\<fileassociation — > element](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)