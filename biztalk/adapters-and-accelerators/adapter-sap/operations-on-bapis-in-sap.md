---
title: "Opérations sur les BAPI dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAPI, operations
- BAPIs, operations on
- Business Application Programming Interface
- BAPIs
- BAPI, transactions
- BAPI transactions, limitations on
ms.assetid: 6be26641-e8d3-4e11-8d82-4fdb13076580
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8504dd05c671307085d621c474969a70026d2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-bapis-in-sap"></a>Opérations sur les BAPI dans SAP
Une Application Programming Interface (BAPI) d’entreprise est une méthode d’un objet métier SAP qui peut être appelée par un processus externe. Interfaces BAPI sont transactionnelles sur le système SAP.  
  
 Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge BAPI appelle dans la direction sortante. Il met en évidence des interfaces BAPI de deux manières :  
  
-   **En tant que RFC**. Vous pouvez appeler une commande BAPI directement par l’appel de la RFC appropriée.  
  
-   **En tant que méthodes d’objets métier**. L’adaptateur met en évidence des interfaces BAPI en tant que méthodes d’objets métier pour des raisons pratiques pour vous aider à récupérer des métadonnées lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].  
  
> [!IMPORTANT]
>  Vous pouvez appeler une commande BAPI sur la carte en tant que RFC ou en tant que méthode d’un objet métier ; mais, quelle que soit la façon dont vous appelez BAPI sur la carte, il appelle toujours BAPI sur SAP via l’interface RFC.  
  
 L’adaptateur prend en charge les transactions BAPI. Le modèle de transaction BAPI sur SAP permet aux utilisateurs de combiner plusieurs interfaces BAPI en une seule unité logique de travail (LUW). Un LUW SAP se compose de toutes les étapes impliquées dans une transaction de mise à jour de la base de données.  
  
 Les rubriques de cette section expliquent comment les interfaces BAPI sont signalées en tant qu’objets métier et comment les transactions BAPI (LUWs) sont prises en charge par l’adaptateur.  
 
  
## <a name="bapi-operations-as-business-object-methods"></a>Opérations BAPI (en tant que méthodes d’objet métier)  
 L’adaptateur met en évidence des interfaces BAPI comme méthodes d’objets métier pour des raisons pratiques pour vous aider à récupérer des métadonnées lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. L’adaptateur appelle toujours BAPI sur le système SAP à l’aide de l’interface RFC.  
  
 L’adaptateur met en évidence des interfaces BAPI par nom en tant qu’opérations sous l’objet métier appropriée pour les opérations sortantes. Les objets métier sont collectés par le groupe fonctionnel sous le nœud de catégorie BAPI par l’adaptateur. (Vous pouvez parcourir ou rechercher des objets métier et des interfaces BAPI sous le **BAPI** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les éléments suivants sur les interfaces BAPI :  
  
-   Paramètres d’importation  
  
-   Paramètres d’exportation  
  
-   MODIFICATION des paramètres  
  
-   Paramètres table  
  
 Pour plus d’informations sur les structures de message et les actions de SOAP utilisées pour les interfaces BAPI exposés en tant que méthodes d’objet métier, consultez [des schémas de Message pour des opérations BAPI](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md).  
  
## <a name="bapi-transactions"></a>Transactions BAPI  
 Lorsque vous appelez un BAPI, il fait toujours partie d’un LUW sur le système SAP. Cela est vrai si vous appelez BAPI sous la forme d’une demande de changement ou une méthode d’un objet métier. Le SDK RFC traite toutes les interfaces BAPI envoyés sur la même connexion SAP dans le cadre de la même LUW. Après un appel à valider ou restaurer la transaction sur une connexion, envoyé via la connexion BAPI suivant commence un nouveau LUW.  
  
 Vous appelez BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK pour valider ou annuler la transaction. L’adaptateur met en évidence ces interfaces deux BAPI :  
  
-   Sous le nœud de base en tant qu’opérations de RFC.  
  
-   Sous chaque objet de l’entreprise.  
  
 Vous contrôlez les BAPI dans une transaction en s’assurant qu’elles sont toutes envoyées via la même connexion SAP (y compris l’appel à valider ou restaurer la transaction). Vous pouvez le faire dans :  
  
-   Les Solutions BizTalk à l’aide de la **ConnectionState** propriété de contexte pour vérifier que les interfaces BAPI dans une transaction sont envoyées à l’aide de la même connexion. Cette propriété est visible par l’adaptateur et vous fournit un contrôle explicite sur la connexion utilisée pour envoyer un message dans une orchestration BizTalk.  
  
     Pour effectuer des transactions BAPI à l’aide de BizTalk Server, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les propriétés de contexte de message suivant.  
  
    |Champ| Description|  
    |-----------|-----------------|  
    |OPEN|Ouvre un nouveau canal pour la transaction.|  
    |RÉUTILISER|Réutiliser un canal existant pour la transaction.|  
    |CLOSE|Valider la transaction et fermer le canal existant.|  
    |ABANDON|Abandonner la transaction et fermer le canal existant.|  
  
     Pour plus d’informations, consultez [exécuter des Transactions BAPI dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md).  
  
    > [!NOTE]
    >  Veillez à définir le **EnableBizTalkCompatibilityMode**propriété de liaison lors de l’exécution de transactions à l’aide de BizTalk Server.  
  
-   Solutions de modèle de service WCF en vous assurant que les interfaces BAPI dans une transaction sont envoyées à l’aide du même client WCF. Pour plus d’informations, consultez [appeler les BAPI dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md).  
  
-   WCF canal solutions de modèles en veillant à ce que les interfaces BAPI dans une transaction sont envoyés sur le même canal WCF. Pour plus d’informations, consultez [développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).  
  
### <a name="limitations-on-bapi-transactions"></a>Limitations sur les Transactions BAPI  
 Les restrictions suivantes s’appliquent sur des transactions BAPI :  
  
-   Il n’est pas possible d’effectuer deux accès en écriture sur la même instance dans un LUW. Par exemple, vous ne peut pas créer une commande et mettre à jour dans la même transaction.  
  
-   Lors de l’exécution d’une transaction à l’aide de BAPI [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], tous les messages doivent être envoyées dans une seule instance d’hôte du port d’envoi.  
  
-   Si une instance est créée, mis à jour ou supprimée à l’aide d’une écriture BAPI, une lecture BAPI ne peut pas afficher les données les plus récentes, jusqu'à ce que l’écriture BAPI est validée.  
  
-   Un client externe qui appelle un LUW doit appeler toutes les interfaces BAPI contenant le LUW sur la même connexion SAP.  
  
> [!IMPORTANT]
>  Interfaces BAPI qui appartiennent à la version 3.1 appellent valider le travail dans le cadre de leur implémentation. Cela signifie que ces interfaces BAPI ne peut pas être inclus avec les autres interfaces BAPI dans un LUW (car ils valide la transaction). Pour plus d’informations, consultez la documentation de SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)