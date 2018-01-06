---
title: "Porady: Tworzenie skojarzeń plików dla aplikacji ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: c6d0a2c0912b98995bb6d933766a46f4ebc527a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Porady: tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikacje mogą być skojarzony z jedną lub więcej rozszerzeń nazw plików, dzięki czemu aplikacja zostanie uruchomiony automatycznie, gdy użytkownik otwiera plik tych typów. Dodawanie obsługi rozszerzenia nazw plików do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji jest prosta.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce  
  
1.  Utwórz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zwykle, lub użyj istniejącą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
2.  Otwórz plik manifestu aplikacji z tekstu lub edytora XML, takiego jak Notatnik.  
  
3.  Znajdź `assembly` elementu. Aby uzyskać więcej informacji, zobacz [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Jako element podrzędny `assembly` elementu, Dodaj `fileAssociation` elementu. `fileAssociation` Element ma cztery atrybuty:  
  
    -   `extension`Rozszerzenie nazwy pliku, które chcesz skojarzyć z aplikacją.  
  
    -   `description`Opis typ pliku, który będzie wyświetlany w powłoce systemu Windows.  
  
    -   `progid`: Ciąg unikatowo identyfikujący typ plików, aby oznaczyć go w rejestrze.  
  
    -   `defaultIcon`: Ikonę do używania tego typu pliku. Ikona muszą zostać dodane jako zasób pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Przykład `file` i `fileAssociation` elementów, zobacz [ \<fileAssociation > elementu](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementy. Należy pamiętać, że `progid` atrybut powinien być inne dla każdego.  
  
6.  Po zakończeniu manifest aplikacji, należy ponownie podpisać plik manifestu. Można to zrobić z wiersza polecenia przy użyciu Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Aby uzyskać więcej informacji, zobacz [Mage.exe (narzędzie do edycji i generowanie manifestu)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Zobacz też  
 [\<fileAssociation > — Element](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)