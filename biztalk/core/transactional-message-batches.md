---
title: Lots de messages transactionnels | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1790c05-e3f7-4667-8a9e-f6f208e55e40
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28be423aa500ba8950b5b2100ce68dba7743bd79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactional-message-batches"></a>Lots de messages transactionnels
Certains adaptateurs doivent coordonner une transaction externe avec une transaction [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interne. Par exemple, l'adaptateur SQL fourni avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit coordonner une transaction [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] avec une transaction [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour ce faire, il doit accéder à l'objet de transaction [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Un objet de transaction est explicitement créé et associé avec le lot avant l'envoi de celui-ci à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Un lot auquel est associé un objet de transaction est appelé « lot transactionnel ». En fournissant votre propre objet de transaction MSDTC (Microsoft Distributed Transaction Coordinator), vous pouvez obtenir la livraison « garantie unique » des données dans et hors de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les adaptateurs de base de données transactionnels tels que l'adaptateur SQL peuvent être sujets à des blocages dans la base de données externes en raison de la transaction unique utilisée pour le lot. C'est pour cette raison que la taille de lot pour l'adaptateur SQL est codée en dur à la valeur un.  
  
 Si l'adaptateur doit inscrire des gestionnaires de ressources supplémentaires, tels qu'une autre base de données ou MSMQ, au sein de l'étendue de cette transaction, il doit créer une transaction externe explicite et la transmettre au moteur de messagerie. Une transaction externe créée et associée à un lot est appelée « lot transactionnel ». Un adaptateur transactionnel est un adaptateur qui utilise des lots transactionnels en créant explicitement une transaction  MSDTC (Microsoft Distributed Transaction Coordinator) externe.  
  
 L'une des raisons pour lesquelles un adaptateur fournit une transaction à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est de s'assurer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou le système externe dispose d'un enregistrement des données. Cet enregistrement garantit la livraison unique du message.  
  
> [!NOTE]
>  Pour plus d’informations sur MSDTC, consultez la documentation de Distributed Transaction Coordinator à : [http://go.microsoft.com/fwlink/?LinkId=44297](http://go.microsoft.com/fwlink/?LinkId=44297).  
  
 FILE est un exemple d'adaptateur qui n'exige pas d'accès à la transaction car les opérations de fichier externes qu'il gère ne sont pas transactionnelles. Dans ce cas, l'adaptateur ne fournit pas d'objet de transaction à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. D'autre part, l'adaptateur SQL interagit avec une base de données SQL et peut avoir d'autres opérations en dehors de ses interactions de message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur peut dans ce cas transmettre une transaction MSDTC externe à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [La gestion des Transactions](../core/handling-transactions.md)