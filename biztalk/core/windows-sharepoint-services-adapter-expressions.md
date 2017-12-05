---
title: "Expressions de l’adaptateur de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- macros, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], supported macros
- configuring [Windows SharePoint Services adapters], expressions
- Windows SharePoint Services adapters, expressions
ms.assetid: 15e3afb2-0ef8-41b4-b3ec-de84af738c12
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 377859a1b2c28774342c6ff9dc5cc312c9fd82d9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="windows-sharepoint-services-adapter-expressions"></a>Expressions de l'adaptateur Windows SharePoint Services
Cette rubrique décrit le format et la signification des chaînes qui peuvent être spécifiées en tant que valeurs pour le **fichier NameProperty Source** propriétés de l’adaptateur Windows SharePoint Services. Elle décrit également les propriétés de contexte associées **WSS. Nom de fichier** et **WSS. ConfigPropertiesXml**. Ces expressions permettent de définir aisément la valeur de nom de fichier ou la valeur de colonne Windows SharePoint Service personnalisée, à l'aide de littéraux et de valeurs extraites du message ou du système BizTalk.  
  
 Les expressions peuvent contenir des littéraux et des macros. Les littéraux apparaissent dans le nom de fichier tels que vous les avez tapés. Les macros doivent être placées entre des caractères « % ». Par exemple, la macro `%MessageID%` est remplacée par le GUID du message au moment de l'exécution.  
  
> [!NOTE]
>  Lorsque le caractère « % » est utilisé comme un littéral ou dans une expression XPATH, celui-ci doit être échappé ainsi \\%. Un seul % sera considéré comme un délimiteur de macro, où un \\% sera remplacé par un seul % lors de l’exécution. Le \ caractère doit être échappé ainsi \\ \\.  
  
## <a name="expression-examples"></a>Exemples d'expression  
  
|Valeur au moment de la conception|Valeur au moment de l'exécution|  
|-----------------------|-------------------|  
|XYZ|XYZ|  
|PurchaseOrder|PurchaseOrder|  
|%MessageID%|55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|PurchaseOrder - %MessageID%|PurchaseOrder - 55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|Remise \\% 10.|Discount %10|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – 10001|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:PartnerName%-%XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – Contoso-10001|  
  
## <a name="supported-macros"></a>Macros prises en charge  
  
|Valeur au moment de la conception|Valeur au moment de l'exécution|  
|-----------------------|-------------------|  
|%MessageID%|ID de message BizTalk qui est un GUID unique.|  
|%SendingOrchestrationID%|ID BizTalk de l'instance d'orchestration dont provient le message.|  
|%SendingOrchestrationType%|Nom de type de l'orchestration dont provient le message.|  
|% XPATH =\<xpath\>%|Permet de spécifier une syntaxe XPATH à utiliser pour extraire la valeur du message. «\<xpath\>» doit être remplacé par une expression XPATH valide. **Remarque :** l’alias d’espace de noms doit être défini en dehors de l’expression dans le 'Alias Namespace' ou WSS. Champ de ConfigNamespaceAliases.|  
|%Filename%|Remplacé par la valeur de nom de fichier extraite de la propriété de contexte de message WSS.Filename. La valeur de la propriété de contexte WSS.Filename des messages reçus de SharePoint est définie sur le nom du fichier SharePoint. La valeur renvoyée est prétraitée à l'aide de la méthode Path.GetFilenameWithoutExtension. **Remarque :** cette macro ne peut pas être utilisée dans WSS. Configuration * Propriétés de contexte (à partir d’orchestration).|  
|%Extension%|Remplacé par la valeur d'extension de fichier extraite de la propriété de contexte de message WSS.Filename. La valeur de la propriété de contexte WSS.Filename des messages reçus de SharePoint est définie sur le nom du fichier SharePoint. La valeur renvoyée est prétraitée à l'aide de la méthode Path.GetExtension. La valeur renvoyée ne contient pas le caractère « . ». **Remarque :** cette macro ne peut pas être utilisée dans WSS. Configuration * Propriétés de contexte (à partir d’orchestration).|  
  
 Les expressions valides prises en charge par la promotion de propriétés constituent des noms de fichier valides au moment de la conception. Les noms de fichier au moment de la conception sont développés lors de l'exécution en noms de fichier Windows SharePoint Services. Les limites applicables aux noms de fichier Windows SharePoint Services sont décrites ci-après.  
  
-   Un nom de fichier Windows valide peut contenir des caractères Unicode, à l'exception des caractères suivants : /  \  :  *  ?  < > &#124;  « # {} % & ~ ou caractères de tabulation et points multiples.  
  
-   Un nom de fichier peut inclure jusqu'à 256 caractères, de même que l'URL entière.  
  
-   Si le nom de fichier Windows SharePoint Services complet contient des caractères non valides, ou si le nom de fichier complet et/ou l'URL sont trop longs, une erreur est consignée dans le journal des événements de l'application et le message est suspendu. L'erreur et l'état du message sont également visibles dans la page Hub du groupe via le suivi des messages et des instances de service.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer Windows SharePoint Services emplacement de réception](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [Comment configurer un gestionnaire d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Types de colonnes Windows SharePoint Services pris en charge](../core/supported-windows-sharepoint-services-column-types.md)