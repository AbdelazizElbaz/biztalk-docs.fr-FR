---
title: "À l’aide de l’adressage IPv6 avec les adaptateurs BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93cd2ead-5e87-47ac-8f78-d56b80afd34e
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5726d5b05c548fd728228fcad39e56ce535fbb5
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="using-ipv6-addressing-with-biztalk-adapters"></a>Utilisation de l'adressage IPv6 avec des adaptateurs BizTalk
Adaptateurs BizTalk Server prend en charge l’utilisation de l’adressage IPv6. Cette rubrique décrit la nomenclature de spécification d'une adresse IPv6 pour un chemin d'accès UNC, la nomenclature de spécification d'une adresse IPv6 littérale et l'utilisation des identificateurs d'étendue IPv6 avec les adaptateurs HTTP et SOAP.  
  
## <a name="ipv6-address-nomenclature-used-for-a-unc-path"></a>Nomenclature d'adresse IPv6 utilisée pour un chemin d'accès UNC  
 Pour spécifier une adresse IPv6 littérale dans un chemin d'accès UNC, procédez comme suit :  
  
1.  Remplacer n’importe quel signe deux-points « : » par des tirets «- » caractères.  
  
2.  Ajoutez le texte «**IPv6 literal.net**» à l’adresse IP.  
  
 Par exemple, la nomenclature d'un URI pointant vers un partage de fichiers sur un ordinateur avec l'adresse IPv6 2001:DB8:2a:1005:230:48ff:fe73:989d serait comme suit :  
  
```  
\\2001-DB8-2a-1005-230-48ff-fe73-989d.ipv6-literal.net\<sharename\>  
```  
  
 Où \< *nom_partage* \> est le nom du partage de fichiers sur l’ordinateur cible.  
  
> [!NOTE]
>  Assurez-vous que les comptes d'utilisateur pour les instances d'hôte dans lesquelles les gestionnaires d'envoi et de réception FILE sont exécutés disposent des autorisations appropriées sur le partage de fichiers. Pour plus d’informations sur les autorisations de dossier requises pour recevoir des fichiers avec l’adaptateur File, consultez [configurer un gestionnaire de réception de fichier](../core/configure-the-file-adapter.md). Pour plus d’informations sur les autorisations de dossier requises lors de l’envoi de fichiers avec l’adaptateur File, consultez [problèmes connus avec l’adaptateur File](../core/known-issues-with-the-file-adapter.md). Pour plus d’informations sur les systèmes de fichiers qui sont pris en charge pour une utilisation avec l’adaptateur File, consultez [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070).  
  
## <a name="using-ipv6-scope-identifiers-with-the-http-adapter-and-the-soap-send-adapter"></a>Utilisation des identificateurs d'étendue IPv6 avec l'adaptateur HTTP et l'adaptateur d'envoi SOAP  
 Adaptateur de réception et d’envoi HTTP et l’adaptateur d’envoi SOAP requièrent que si un identificateur de portée est utilisé dans une adresse IPv6, l’identificateur de portée doit être échappé avec le code d’échappement **% 25**. Par exemple, **fe80::550c:489f:e65e:aef3 %8** est une adresse IPv6 valide contenant un identificateur de portée (%8). Pour utiliser cette adresse IPv6 avec les adaptateurs d'envoi et de réception HTTP ou l'adaptateur d'envoi SOAP, l'identificateur d'étendue doit être assorti d'un caractère d'échappement comme suit :  
  
```  
fe80::550c:489f:e65e:aef3%258  
```  
  
## <a name="adapter-uri-nomenclature-used-for-a-literal-ipv6-address"></a>Nomenclature d'un URI d'adaptateur utilisée pour une adresse IPv6 littérale  
  
-   Pour utiliser une adresse IPv6 littérale pour un URI d'adaptateur, placez l'adresse IP entre crochets (« [ », « ] »). Par exemple, la nomenclature d'un URI avec l'adresse IPv6 2001:DB8:2a:1005:230:48ff:fe73:989d serait comme suit :  
  
    ```  
    [2001:DB8:2a:1005:230:48ff:fe73:989d]  
    ```  
  
    > [!NOTE]
    >  L’utilisation du littéral d’une adresse IPv6 pour l’URI d’adaptateur suit les règles établies dans [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375).  
  
-   Lorsqu'une adresse IPv6 littérale est spécifiée comme nom du serveur pour l'adaptateur de réception POP3, l'adaptateur d'envoi SMTP ou les adaptateurs d'envoi et de réception SQL, l'adresse IPv6 ne doit pas être placée entre crochets.  
  
## <a name="summary-of-considerations-when-using-literal-ipv6-addressing-with-biztalk-adapters"></a>Résumé des considérations relatives à l'utilisation de l'adressage IPv6 littéral avec les adaptateurs BizTalk  
 Le tableau suivant indique quand l'utilisation d'une adresse IPv6 littérale nécessite que l'adresse IP soit placée entre crochets (« [ », « ] ») et quand un identificateur d'étendue utilisé dans une adresse IPv6 doit être assorti d'un caractère d'échappement :  
  
|Adaptateur|Nécessite que l'adresse IPv6 littérale soit placée entre crochets ?|Nécessite que l'identificateur d'étendue soit assorti d'un caractère d'échappement ?|  
|---|---|---|  
|Réception POP3|non|non|  
|Envoi SMTP|non|non|  
|Envoi et réception SQL|non|non|  
|Envoi et réception FILE|Non (voir la section **Nomenclature d’adresse IPv6 utilisée pour un chemin d’accès UNC**)|non|  
|Envoi et réception HTTP|Oui|Oui|  
|Envoi et réception MQSeries|Oui|non|  
|Envoi et réception MSMQ|Oui|non|  
|Envoi SOAP|Oui|Oui|  
|Réception SOAP|Oui|non|  
|Envoi et réception WCF|Oui|non|