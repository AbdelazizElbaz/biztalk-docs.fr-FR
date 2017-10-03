---
title: "Configuration des propriétés d’accord AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.as2agreement.properties
ms.assetid: a62d8d2a-0b8d-4179-a48f-92f135b5787d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a6f09f85b726869e98712abf354ad3943ce97a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-agreement-properties"></a>Configuration des propriétés de l'accord AS2
Cette section décrit les propriétés d'accord sur le transport AS2. Dans les paramètres du protocole de transport, vous pouvez également définir si le message doit être signé, chiffré, etc.  
  
> [!NOTE]
>  La configuration d'un accord AS2 est facultative. Un accord AS2 définit la manière dont les messages sont transférés à l'aide du protocole AS2. Si les partenaires commerciaux décident d'utiliser un autre protocole de transport pour transférer des messages, ils peuvent décider de ne pas définir d'accord AS2. En revanche, les partenaires commerciaux doivent définir un accord sur le codage régissant la manière dont les messages sont formés et codés. Pour plus d’informations sur les contrats de codage, consultez [configuration des propriétés d’encodage de l’accord](../core/configuring-encoding-agreement-properties.md).  
  
> [!IMPORTANT]
>  Lorsque vous modifiez un paramètre AS2 dans un accord, vous devez redémarrer l'instance de l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour que les modifications prennent effet.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md)  
  
-   [Configuration des identificateurs (AS2)](../core/configuring-identifiers-as2.md)  
  
-   [Validation de la configuration (AS2)](../core/configuring-validation-as2.md)  
  
-   [Configuration des accusés de réception (MDN) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)  
  
-   [Configuration des paramètres de l’hôte Local (AS2)](../core/configuring-local-host-settings-as2.md)  
  
-   [Configuration des certificats de Signature (AS2)](../core/configuring-signature-certificates-as2.md)  
  
-   [Configuration de l’Association de Port d’envoi (AS2)](../core/configuring-send-port-association-as2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés AS2](../core/configuring-as2-properties.md)