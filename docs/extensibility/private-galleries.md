---
title: Galerie prywatnego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c58ce16489c02475a7d76327e9df19a6022109a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="private-galleries"></a>Galerie prywatnych
Formanty, szablony i narzędzia tworzonych przez ich firmę można udostępniać *prywatnej galerii* w sieci intranet dla organizacji, w następujący sposób:  
  
-   Utwórz Atom () źródło danych RSS do odpowiednio skonfigurowanego centralną lokalizację (repozytorium) w sieci intranet. Aby uzyskać więcej informacji, zobacz [jak: utworzyć źródło danych Atom galerii prywatnego](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Dystrybuuj pliku .pkgdef, który opisuje prywatnej galerii. Zalecamy, aby ta konfiguracja dla administratorów, którzy chcą nawiązywać połączenia prywatnej galerii na wielu komputerach jednocześnie.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dodawanie galerii prywatnych do rozszerzenia i aktualizacje w programie Visual Studio  
 Gdy galerii prywatny jest dostępny, można dodać go do **rozszerzenia i aktualizacje** w programie Visual Studio.  
  
 ![Okno dialogowe dodawania Menedżera rozszerzenia](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Aby dodać prywatnej galerii do rozszerzenia i aktualizacje  
  
1.  Na pasku menu wybierz **narzędzia**, **opcje**.  
  
2.  W **środowiska** węzła, wybierz opcję **rozszerzenia i aktualizacje**.  
  
3.  Wybierz **Dodaj** przycisku.  
  
4.  W **nazwa** wprowadź nazwę prywatnej galerii, na przykład `My Gallery`.  
  
5.  W **adres URL** wprowadź adres URL źródła danych Atom lub witryny programu SharePoint, w której uruchomiono prywatnej galerii.  
  
    1.  Jeśli host znajduje się źródło danych Atom łączące się prywatnej galerii, adres URL będzie przypominać ten: http://www.mywebsite/mygallery/atom.xml.  Ten adres URL może odwoływać się do pliku lub ścieżkę sieciową.  
  
    2.  Jeśli host jest witryną programu SharePoint, adres URL będzie przypominać ten: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Zarządzanie galerie prywatnych  
 Administrator może udostępnić prywatnej galerii na wielu komputerach jednocześnie przez modyfikację rejestru systemu na każdym komputerze. W tym celu należy utworzyć plik .pkgdef, który opisuje nowych kluczy rejestru i ich wartości.  Format ten plik ma następującą składnię.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie prywatnej galerii przez za pomocą ustawień rejestru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalowanie rozszerzeń z galerii prywatnych  
 Można wyszukiwać i zainstalować rozszerzenia programu Visual Studio z galerii prywatnych w **rozszerzenia i aktualizacje**. Poniższe kroki użycia prywatnych galerii o nazwie `My Gallery`.  
  
 ![Instalowanie galerii prywatnego Menedżera rozszerzenia](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Wyszukaj i zainstaluj rozszerzenia z galerii prywatnych  
  
1.  Na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie wybierz **rozszerzeń Online**, a następnie wybierz **Moje galerii**.  
  
3.  W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz pozycję **Pobierz** przycisku.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Aktualizacja rozszerzeń z galerii prywatnych  
 Jak nowe wersje rozszerzeń programu Visual Studio są opublikowane w galerii prywatnych, należy zaktualizować rozszerzenia, które zostały zainstalowane. Poniższe kroki użycia prywatnych galerii o nazwie `My Repository`.  
  
 ![Aktualizacja galerii prywatnego Menedżera rozszerzenia](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aby zaktualizować zainstalowanego rozszerzenia z galerii prywatnych  
  
1.  Na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
2.  W okienku po lewej stronie wybierz **aktualizacje**, a następnie wybierz **Moje repozytorium**.  
  
3.  W okienku po prawej stronie zaznacz rozszerzenie, a następnie wybierz pozycję **aktualizacji** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie rozszerzeń programu Visual Studio i korzystanie](../ide/finding-and-using-visual-studio-extensions.md)   
 [Wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)