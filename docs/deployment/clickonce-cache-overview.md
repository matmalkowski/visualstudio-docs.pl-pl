---
title: Przegląd pamięci podręcznej ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff72cd106f39b4573a0e1d61715dad4f8c65140
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31564925"
---
# <a name="clickonce-cache-overview"></a>Przegląd pamięci podręcznej w technologii ClickOnce
Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, czy są one zainstalowane lokalnie lub hostowanych w trybie online są przechowywane na komputerze klienckim w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikacji *pamięci podręcznej*. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej to rodzina ukrytych katalogów w katalogu lokalnym ustawienia folderu Dokumenty i ustawienia bieżącego użytkownika. Ta pamięć podręczna przechowuje pliki wszystkich aplikacji, w tym zestawy, pliki konfiguracji, aplikacji i ustawień użytkownika i katalog danych. Pamięć podręczna również jest odpowiedzialny za migracji katalogu danych do najnowszej wersji. Aby uzyskać więcej informacji na temat migracji danych, zobacz [dostęp do lokalnych i zdalnych danych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Zapewniając pojedynczą lokalizację magazynu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przejmuje zadań związanych z zarządzaniem fizycznej instalacji aplikacji przez użytkownika. Pamięć podręczna pomaga również w izolowania aplikacji dzięki przechowywaniu plików danych dla wszystkich aplikacji i zestawy i ich różne wersje oddzielić od siebie nawzajem. Na przykład po uaktualnieniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, wersji i jej zasoby danych dostarczanych z ich własnych katalogów w pamięci podręcznej.  
  
## <a name="cache-storage-quota"></a>Przydział pamięci masowej w pamięci podręcznej  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, które są obsługiwane w trybie online są ograniczone ilości miejsca może zajmują przez przydziału, która ogranicza rozmiar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pamięci podręcznej. Rozmiar pamięci podręcznej ma zastosowanie do wszystkich użytkowników aplikacji online; pojedynczej aplikacji częściowo zaufany, online jest ograniczona do zajmujące połowy limitu przydziału miejsca. Zainstalowane aplikacje nie są ograniczone przez rozmiar pamięci podręcznej i nie są uwzględniane limit pamięci podręcznej. Dla wszystkich [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, pamięci podręcznej zachowuje bieżącej wersji i wcześniej zainstalowanej wersji.  
  
 Domyślnie komputery klienckie mają 250 MB przestrzeni dyskowej na online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Pliki danych nie są wliczane do tego limitu. Administrator systemu może zwiększenia lub zmniejszenia ten limit przydziału na komputerze klienckim w szczególności, zmieniając klucz rejestru HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, czyli wartość DWORD który określa rozmiar pamięci podręcznej w kilobajtach. Na przykład aby zmniejszyć rozmiar pamięci podręcznej do 50 MB, czy Zmień tę wartość na 51200.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)