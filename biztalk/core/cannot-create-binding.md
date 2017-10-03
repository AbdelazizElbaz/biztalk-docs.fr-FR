---
title: "Ne peut pas créer de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbe1bd54-6031-4f90-a445-c1647b382a1a
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 227addce4f5a5c1d6d18b7e21646e5276732a28f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-create-binding"></a>Impossible de créer la liaison
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de créer la liaison car le type de liaison n'est pas indiqué. Spécifiez un type de liaison tel que « basicHttpBinding », « wsHttpBinding » ou « customBinding »|  
  
## <a name="explanation"></a>Explication  
 Vous n'avez pas défini la propriété BindingType dans le code après la configuration d'un transport WCF-Custom ou WCF-CustomIsolated. Le problème peut également provenir d'autres chemins d'accès au code. Le paramètre de liaison doit être associé à une valeur dans l'interface utilisateur. Vérifiez votre configuration et assurez-vous qu'un type de liaison a été choisi dans la liste déroulante de la zone Propriétés de l'emplacement de réception.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez le code de configuration du transport WCF-Custom ou WCF-CustomIsolated. Vérifiez que le **BindingType** propriété dans les données XML pour le **TransportTypeData** propriété de l’interface ITransportInfo est définie correctement.  
  
 En outre, spécifiez un type de liaison **basicHttpBinding**, **wsHttpBinding**, ou **customBinding**.  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Vérifiez qu’une valeur est spécifiée dans le **Type de liaison** liste.  
  
 Pour plus d'informations sur la configuration des liaisons, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Pour configurer les emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-Custom](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [Comment configurer un Port d’envoi WCF-Custom](../core/how-to-configure-a-wcf-custom-send-port.md)