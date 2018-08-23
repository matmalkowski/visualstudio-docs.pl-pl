---
title: Aby zarejestrować rozszerzenie za pomocą atrybutu niestandardowego rejestracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: douge
ms.openlocfilehash: e94d6a674590430e0635c297f21be9d356c56a71
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678002"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Aby zarejestrować rozszerzenie za pomocą atrybutu niestandardowego rejestrowania
W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Można użyć atrybutów rejestracji, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi pochodzić od klasy <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, i musi ono przesłonić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> i <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody.  
  
## <a name="creating-a-custom-attribute"></a>Tworzenie atrybutów niestandardowych  
 Poniższy kod przedstawia sposób tworzenia nowego atrybutu rejestracji.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> Na klasy atrybutów służy do określenia elementu programu, (klasy, metody itp.), do którego odnoszą się atrybut, czy może służyć więcej niż jeden raz i czy mogą być dziedziczone.  
  
### <a name="creating-a-registry-key"></a>Tworzenie klucza rejestru  
 Poniższy kod powoduje utworzenie niestandardowego atrybutu **niestandardowe** podkluczy klucza dla pakietu VSPackage, który jest rejestrowany.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości w ramach istniejącego klucza rejestru  
 Wartości niestandardowe można dodać do istniejącego klucza. Poniższy kod przedstawia sposób dodawania nowej wartości z kluczem rejestracji pakietu VSPackage.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```