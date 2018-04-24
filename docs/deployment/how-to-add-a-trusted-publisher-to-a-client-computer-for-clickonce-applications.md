---
title: 'Porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c9d718eba01a35c1f6991ab50d217c8b5f63065
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Porady: dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
Wdrażanie zaufanej aplikacji można skonfigurować komputery klienckie, aby Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są uruchamiane na wyższym poziomie zaufania bez monitowania użytkownika. Poniższe procedury pokazują, jak dodać certyfikat wydawcy do magazynu zaufanych wydawców na komputerze klienckim za pomocą narzędzia wiersza polecenia CertMgr.exe.  
  
 Polecenia, których można się nieco różnić w zależności od tego, czy urząd certyfikacji (CA), który wystawił certyfikat jest częścią zaufanych certyfikatów głównych do klienta. Jeśli komputer kliencki z systemem Windows jest częścią domeny, będzie zawierać, na liście, są traktowane jako certyfikatów zaufanych głównych urzędów certyfikacji. Ta lista jest zazwyczaj skonfigurowany przez administratora systemu. Jeśli certyfikat został wystawiony przez jeden z tych zaufanych certyfikatów głównych lub przez urząd certyfikacji który tworzy łańcuch do jednej z tych zaufanych certyfikatów głównych, można dodać certyfikatu do magazynu zaufanych certyfikatów głównych klienta. Jeśli z drugiej strony, certyfikat nie został wystawiony przez jeden z tych zaufanych certyfikatów głównych, należy dodać certyfikatu do klienta magazynu zaufanych certyfikatów głównych i magazynie zaufanego wydawcę.  
  
> [!NOTE]
>  Należy dodać certyfikaty w ten sposób na każdym komputerze klienta, do której ma zostać umieszczony [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wymagającej z podwyższonym poziomem uprawnień. Certyfikaty można dodać ręcznie lub za pośrednictwem aplikacji wdrażanych dla klientów. Należy skonfigurować te komputery raz, po którym można wdrażać dowolną liczbę [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane przy użyciu tego samego certyfikatu.  
  
 Możesz też dodać certyfikatu do magazynu, programowo przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Store> klasy.  
  
 Przegląd wdrażania zaufanych aplikacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Dodawanie certyfikatu do magazynu zaufanych wydawców w obszarze zaufanego głównego  
  
1.  Uzyskaj certyfikat od urzędu certyfikacji.  
  
2.  Eksportowanie certyfikatu w formacie Base64 X.509 (.cer). Aby uzyskać więcej informacji na temat formatów certyfikatu, zobacz [eksportowanie certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj prywatne - c -s - r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Dodawanie certyfikatu do magazynu zaufanych wydawców różnych głównych  
  
1.  Uzyskaj certyfikat od urzędu certyfikacji.  
  
2.  Eksportowanie certyfikatu w formacie Base64 X.509 (.cer). Aby uzyskać więcej informacji na temat formatów certyfikatu, zobacz [eksportowanie certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine głównego**  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Porady: włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Instrukcje: konfigurowanie funkcji zaufanego monitowania technologii ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)