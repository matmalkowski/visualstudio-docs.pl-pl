---
title: Zaufania rozwiązań pakietu Office przy użyciu list dołączania
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e2fea115b941af4b119b59dade16114cab3383d
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844228"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Zaufania rozwiązań pakietu Office przy użyciu list dołączania
  Listy dołączania użytkownicy udzielenia zaufania do rozwiązań pakietu Office, które są podpisane za pomocą certyfikatu, który identyfikuje wydawcy. Listy dołączania są specyficzne dla użytkownika i może służyć do dostosowania na poziomie dokumentu i dodatków narzędzi VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Gdy użytkownik uruchamia rozwiązania do pakietu Office, które nie zostały przyznane zaufania dla danego użytkownika, rozwiązania Microsoft Office wyświetla monit o jej decyzji zabezpieczeń z [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania wiersza. Jeśli użytkownik zdecyduje się na zaufania rozwiązania, uruchamia dostosowania, a użytkownik nie jest monitowany podczas następnego.  
  
## <a name="inclusion-list-and-windows-installer"></a>Lista dołączania i Instalator Windows  
 Instalowanie rozwiązań pakietu Office do *Program Files* katalogu za pomocą Instalatora systemu Windows wymaga uprawnień administratora. Dla rozwiązań pakietu Office w *Program Files* katalogu, ponieważ już przyznano rozwiązań pakietu Office uprawnień FullTrust Visual Studio Tools for Office runtime nie sprawdza lista dołączania.  
  
## <a name="clickonce-trust-prompt"></a>Wiersz zaufania ClickOnce  
 Za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] wdrożenia dla rozwiązań pakietu Office, Administratorzy można skonfigurować poziom monitu zaufania, aby zezwolić na monitowanie, wyłącz monitowania lub wymagają zaufanego certyfikatu. Ta konfiguracja jest implementowana przy użyciu klucza rejestru, która kontroluje dostęp do listy dołączania.  
  
 Jeśli monitowania jest wyłączone, można zainstalować tylko w przypadku rozwiązania, które mają certyfikat zaufanego i znanego. Jeśli poziom sygnalizowania Authenticode wymagane rozwiązania muszą być podpisane przy użyciu certyfikatu ze znanego urzędu, ale nie wymaga certyfikatu, który tworzy łańcuch z zaufanym głównym urzędem (zaufanego certyfikatu). Jeśli monitowania jest dozwolone, rozwiązanie może być podpisany przy użyciu certyfikatu z nieznanych tożsamości. W tym scenariuszu decyzja dotycząca zaufania została odroczona dla użytkownika końcowego, a certyfikat tymczasowego wystarczyć zainstalować rozwiązanie.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zabezpieczeń listy dołączania](../vsto/how-to-configure-inclusion-list-security.md) i tabela 2, zatytułowany monitowania poziom rejestru klucz wartość Uruchom efekty, [ClickOnce Konfigurowanie zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Struktura listy dołączania  
 Włączenie nieprawidłowy wpis na liście ma dwie części: ścieżka do manifestu wdrożenia, a klucz publiczny używany do podpisywania rozwiązania. Po rozwiązaniu zostanie dodany do listy dołączania, jest on uznawany za zaufany. Po uruchomieniu rozwiązania pakietu Office aplikacji pakietu Office porównuje klucza publicznego na liście dołączania przy użyciu klucza podpisywania w manifeście rozmieszczenia, aby sprawdzić, czy rozwiązanie, które jest aktualnie uruchomione jest taki sam, jak oryginalna wersja zaufanych.  
  
## <a name="see-also"></a>Zobacz także  
 [Udziel zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  