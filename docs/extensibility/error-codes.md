---
title: Kody błędów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6feb9bfa3b2adb437fd03b5c0b8d4448df4b6f50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130777"
---
# <a name="error-codes"></a>Kody błędów
Po powrocie z funkcji API dodatku typu Plug-in kontroli źródła wystąpił błąd ma być jedną z następujących kodów błędów. Wszystkie błędy są ujemne, ostrzeżenia i kody błędów informacyjną dodatnia, i Powodzenie wynosi 0.  
  
|Kod błędu|Wartość|Opis|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Wtyczka obsługuje dodawanie plików z kontroli źródła w dwóch krokach. Aby uzyskać więcej informacji, zobacz [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Pliku lokalnego różni się od pliku w bazie danych kontroli źródła (na przykład [SccDiff](../extensibility/sccdiff-function.md) może zwracać wartości).|  
|`SCC_I_RELOADFILE`|5|Lokalny plik został zmieniony podczas operacji kontroli źródła; IDE należy ponownie załadować plik, jeśli to możliwe.|  
|`SCC_I_FILENOTAFFECTED`|4|Nie dotyczy pliku.|  
|`SCC_I_PROJECTCREATED`|3|Projekt został utworzony podczas operacji kontroli źródła (na przykład podczas wywoływania [SccOpenProject](../extensibility/sccopenproject-function.md) podczas `SCC_OP_CREATEIFNEW` określono flagę).|  
|`SCC_I_OPERATIONCANCELED`|2|Operacja została anulowana.|  
|`SCC_I_ADV_SUPPORT`|1|Wtyczka obsługuje zaawansowane opcje dla tego polecenia. Aby uzyskać więcej informacji, zobacz [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Powodzenie.|  
|`SCC_E_INITIALIZEFAILED`|-1|Błąd: nie można zainicjować.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Błąd: projekt jest nieznany.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Błąd: nie można utworzyć projektu.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Błąd: plik nie został wyewidencjonowany.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Błąd: plik został już wyewidencjonowany.|  
|`SCC_E_FILEISLOCKED`|-6|Błąd: plik jest zablokowany.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Błąd: plik jest wyewidencjonowany wyłączność.|  
|`SCC_E_ACCESSFAILURE`|-8|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|`SCC_E_CHECKINCONFLICT`|-9|Błąd: Wystąpił konflikt podczas ewidencjonowania.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Błąd: plik już istnieje.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Błąd: plik nie jest pod kontrolą źródła.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Błąd: plik jest wyewidencjonowany.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Błąd: Brak nie określonej wersji.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Błąd: operacja nie jest obsługiwana.|  
|`SCC_E_NONSPECIFICERROR`|-15|Nieokreślony błąd.|  
|`SCC_E_OPNOTPERFORMED`|-16|Błąd, operacja nie została wykonana.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Błąd: typ pliku, na przykład binarny, nie jest obsługiwany przez system kontroli kodu źródłowego.|  
|`SCC_E_VERIFYMERGE`|-18|Plik został scalony automatycznie, ale nie została sprawdzona, ponieważ jest weryfikacja oczekujące użytkownika.|  
|`SCC_E_FIXMERGE`|-19|Plik został scalony automatycznie, ale nie została sprawdzona w z powodu konfliktu scalania, który należy ręcznie rozwiązać.|  
|`SCC_E_SHELLFAILURE`|-20|Błąd z powodu błędu powłoki.|  
|`SCC_E_INVALIDUSER`|-21|Błąd: użytkownik jest nieprawidłowy.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Błąd: projekt jest już otwarty.|  
|`SCC_E_PROJSYNTAXERR`|-23|Błąd składniowy projektu.|  
|`SCC_E_INVALIDFILEPATH`|-24|Błąd: ścieżka pliku jest nieprawidłowa.|  
|`SCC_E_PROJNOTOPEN`|-25|Błąd: projekt nie jest otwarty.|  
|`SCC_E_NOTAUTHORIZED`|-26|Błąd: użytkownik nie ma uprawnień do wykonania tej operacji.|  
|`SCC_E_FILESYNTAXERR`|-27|Błąd składniowy w pliku.|  
|`SCC_E_FILENOTEXIST`|-28|Błąd lokalny plik nie istnieje.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Błąd: Wystąpił błąd połączenia.|  
|`SCC_E_UNKNOWNERROR`|-30|Wystąpił nieznany błąd.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Operacji get w tle jest obecnie w toku.|  
  
## <a name="macros-provided-for-quick-checking"></a>Makra przewidzianych szybkie sprawdzanie  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie funkcje interfejsu API dodatku typu Plug-in kontroli źródła (z wyjątkiem [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), i [SccDiff](../extensibility/sccdiff-function.md)) powinny się powieść po lokalnymi plikami, które są przekazywane jako argumenty nie istnieje w folderze roboczym. Na przykład IDE może wystawiać wywołanie [SccCheckout](../extensibility/scccheckout-function.md) lub [SccUncheckout](../extensibility/sccuncheckout-function.md) na plik, który nie istnieje w folderze pracy, ale nie istnieje w systemie kontroli źródła. To wywołanie powiedzie się. Tylko wtedy, gdy plik w folderze pracy lub w systemie kontroli źródła nie istnieje funkcja powinna zakończyć się niepowodzeniem.  
  
 Niektóre funkcje, takie jak `SccAdd` i `SccCheckin`, w szczególności powinny zwrócić `SCC_E_FILENOTEXIST` Jeśli plik w folderze roboczy nie istnieje. Inne funkcje powinny się podczas pracy plik nie istnieje, jeśli te funkcje działają na prawidłową nazwę pliku w systemie kontroli źródła.  
  
 Wtyczkę kontroli źródła należy wykonać żadnych założeń dotyczących uprawnień do pliku w folderze pracy, nawet jeśli wtyczki miał oznaczone jako plik tylko do odczytu podczas operacji. Plik w folderze pracy można przenieść, usunięte i zmieniony poza plug w kontroli.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)