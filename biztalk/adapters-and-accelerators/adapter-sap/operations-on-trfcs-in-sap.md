---
title: "Opérations sur tRFCs dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RFCs, invoking transactional RFCs in an SAP System
- TID database
- transactional RFCs
- tRFCs, receiving inbound iransactional RFC calls from an SAP system
- tRFCs
- GUID parameter
- RFCs, processing inbound
- RfcConfirmTransID
- transaction ID (TID)
- tRFC Operations
- IDOCS, receiving IDOCs as a tRFC server
- adapters, operations on tRFCs
- RFC, invoking an RFC
ms.assetid: d6a5c515-d6aa-4b70-9c23-32d1dd94d473
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e60465716931161e9b9949e16c4630d85c2cfe2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-trfcs-in-sap"></a>Opérations sur tRFCs dans SAP
RFC transactionnelles (tRFCs) sont les RFC qui sont appelées en tant que partie d’une unité logique de travail (LUW). Sur un système SAP, un LUW contient toutes les étapes nécessaires pour effectuer une entreprise ou une tâche de programmation. Un tRFC représente un moyen d’appeler une commande RFC ; Il n’est pas un artefact SAP unique.  
  
 Vous pouvez utiliser la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] comme un client tRFC et comme un serveur tRFC.  
  
-   **Comme un client tRFC**, l’adaptateur permet à votre application appeler un RFC unique dans un LUW sur le système SAP. Cela garantit l’exécution seule unique de la RFC. Il n’implique pas le comportement transactionnel.  
  
-   **Comme un serveur tRFC**, l’adaptateur vous permet de recevoir plusieurs RFC à l’intérieur d’un LUW. L’adaptateur prend en charge les appels entrants tRFC dans un contexte transactionnel ; qui est la validation et le comportement précédent de restauration sont pris en charge.  
  
## <a name="trfc-operations"></a>Opérations tRFC  
 Un tRFC implique un moyen d’appeler une commande RFC ; Il n’est pas un artefact SAP distinct. Par conséquent, chaque RFC sur le système SAP (pour laquelle l’adaptateur peut récupérer les métadonnées) est également exposé en tant qu’un tRFC par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. tRFCs sont signalées par le nom de la RFC en tant qu’opérations sous le nœud de catégorie de métadonnées TRFC. (Vous pouvez parcourir ou rechercher tRFCs sous le **TRFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les éléments suivants sur tRFCs :  
  
-   Paramètres d’importation  
  
-   MODIFICATION des paramètres (uniquement la partie entrée de la modification de paramètre est pris en charge)  
  
> [!NOTE]
>  tRFCs sont exécutées de façon asynchrone, aucune valeur de sortie (paramètres d’exportation ou de modification) n’est retournées pour les.  
  
 Un paramètre GUID est visible par l’adaptateur pour les opérations tRFC. Ce GUID est mappé par l’adaptateur à la transaction SAP ID (TID) qui est associé à le tRFC. Vous pouvez utiliser ce paramètre GUID pour :  
  
-   Confirmer le tRFC sur le système SAP dans les appels du client tRFC. Pour cela, en appelant l’opération RfcConfirmTransId. Il s’agit d’une opération particulière par l’adaptateur pour confirmer un TID sur le système SAP.  
  
-   Obtenir le TID SAP réelle utilisée pour un tRFC à partir de l’adaptateur au client tRFC et scénarios de serveur tRFC. Pour cela, vous devez en appelant la méthode utilitaire SAP, ConvertGuidToTid.  
  
 Pour plus d’informations sur ces opérations, consultez [des opérations spéciales](../../adapters-and-accelerators/adapter-sap/special-operations.md). Pour plus d’informations sur les structures de message et les actions de SOAP utilisées pour tRFCs par l’adaptateur, consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## <a name="invoking-transactional-rfcs-in-an-sap-system"></a>L’appel de la RFC transactionnels dans un système SAP  
 En règle générale, les tRFCs sont utilisés pour exécuter un ou plusieurs appels RFC à l’intérieur d’un seul LUW ; Toutefois, en raison des limitations dans le SDK de RFC SAP, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge uniquement un seul tRFC par LUW. Pour cette raison, l’adaptateur crée un LUW (TID SAP) pour chaque tRFC. Pour ces clients, SAP définit un LUW comme un mécanisme permettant de garantir l’exécution de « unique » de la RFC et n’implique pas de validation et basé sur la restauration des transactions.  
  
 Les étapes suivantes récapitulent les tâches qui sont exécutées dans un appel de client RFC à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Certaines de ces étapes sont effectuées par le client de carte, et certaines sont effectuées par l’adaptateur.  
  
1.  Le client de l’adaptateur envoie un message de demande pour l’opération tRFC. Le client de l’adaptateur peut éventuellement fournir un GUID dans ce message.  
  
2.  Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] reçoit le message de demande et utilise le SDK RFC pour obtenir une ID (TID) de la transaction à partir du système SAP. Si le message de demande contient un GUID, l’adaptateur mappe ce GUID pour le TID SAP ; dans le cas contraire, l’adaptateur crée un nouveau GUID et le mappe le TID SAP  
  
3.  L’adaptateur utilise le TID pour appeler le tRFC sur le serveur SAP. L’état du TID est marqué comme **terminé** sur le système SAP.  
  
4.  L’adaptateur retourne le GUID (qui est mappé au TID) pour le client de l’adaptateur dans le message de réponse.  
  
5.  Le client de l’adaptateur appelle l’opération RfcConfirmTransID sur la carte avec le GUID retourné à l’étape précédente.  
  
6.  L’adaptateur utilise le GUID dans le message de demande RfcConfirmTransID pour identifier le TID SAP et confirme que l’appel de tRFC sur le système SAP. Cela entraîne le serveur SAP afin de supprimer l’entrée TID sa base de données.  
  
> [!NOTE]
>  appels du client tRFC ne retournent pas de paramètres d’exportation ou de modification.  
  
 Pour plus d’informations sur :  
  
-   Appel d’un tRFC à l’aide de BizTalk Server, consultez [appeler tRFCs dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md).  
  
-   Appel d’un tRFC à l’aide du modèle de service WCF, consultez [appeler tRFCs dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).  
  
-   Structures et action SOAP pour appeler un tRFC des messages, consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## <a name="receiving-inbound-transactional-rfc-calls-from-an-sap-system"></a>Appels entrants RFC transactionnelle réception à partir d’un système SAP  
 Vous pouvez utiliser l’adaptateur comme un serveur tRFC pour recevoir des tRFCs à partir de SAP. En tant que tRFC serveur, lorsque l’adaptateur reçoit un tRFC, appelle l’opération tRFC correspondante sur votre application. L’adaptateur prend en charge les fonctionnalités suivantes lorsqu’il agit comme un serveur tRFC :  
  
-   Un LUW (identifiée par un TID SAP) peut contenir plusieurs tRFCs (RFC appels).  
  
-   L’adaptateur crée une transaction validable pour chaque TID SAP. Code de votre application peut s’inscrire dans cette transaction.  
  
-   La validation et restauration sont pris en charge.  
  
 Le reste de cette section fournit des informations générales sur l’utilisation de l’adaptateur comme un serveur tRFC. Pour plus d’informations sur :  
  
-   Réception d’un tRFC entrant appels à l’aide de BizTalk Server, reportez-vous à la section [tRFC de réception entrant appels à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md).  
  
-   Recevoir un tRFC entrant appels à l’aide du modèle de service WCF, reportez-vous à la section [tRFC de réception entrant appelle dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md).  
  
### <a name="the-tid-database"></a>La base de données TID  
 Lorsqu’il agit comme un serveur tRFC, l’adaptateur utilise une base de données SQL Server, la base de données TID — pour gérer la transaction ID qu’il reçoit à partir du système SAP. Par exemple, il utilise la base de données TID pour aider à gérer les appels à partir du système SAP pour la validation, la restauration, et confirmer le TID. L’adaptateur stocke également le GUID qu’il crée et associe chaque TID SAP dans la base de données TID.  
  
### <a name="prerequisites"></a>Conditions préalables  
 Pour l’adaptateur comme un serveur tRFC, vous devez vous assurer que les conditions suivantes sont remplies :  
  
-   Le document RFC doit être déclaré dans le système SAP. Il s’agit donc de l’adaptateur peut récupérer les métadonnées qui décrivent la RFC à partir du système SAP. Le document RFC est réellement implémenté dans votre application.  
  
-   L’adaptateur doit inscrire avec une destination RFC sur la passerelle SAP. L’inscription est basée sur un nom logique est appelé un ID de programme. Spécifier des paramètres dans l’URI de connexion pour spécifier l’ID de programme, passerelle SAP et le serveur SAP pour cet enregistrement.  
  
-   La base de données TID doit être créée dans SQL Server. Pour ce faire, vous devez exécuter un script SQL qui est installé par le programme d’installation. Le script SQL est généralement installé sur \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [l’installation de BizTalk Adapter Pack](http://msdn.microsoft.com/library/2ae27db5-b11b-42c3-a568-e2331badf80e).  
  
-   Le **TidDatabaseConnectionString** liaison de la propriété doit être définie sur la chaîne de connexion de base de données SQL pour la base de données TID. Pour plus d’informations sur la **TidDatabaseConnectionString** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
> [!NOTE]
>  Définition de la **TidDatabaseConnectionString** propriété de liaison configure l’adaptateur pour agir comme un serveur tRFC plutôt que comme un serveur RFC. Si le **TidDatabaseConnectionString** liaison de la propriété est définie et vous spécifiez une destination RFC dans l’URI de connexion, l’adaptateur fait Office de serveur pour les appels entrants à partir de la destination RFC tRFC. Si cette propriété de liaison n’est pas définie, l’adaptateur agit comme un serveur RFC.  
  
### <a name="how-the-adapter-processes-inbound-trfcs"></a>Comment le tRFCs entrant des processus d’adaptateur  
 Les étapes suivantes récapitulent les tâches qui sont effectuées par l’appel de client RFC à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Certaines de ces étapes sont effectuées par le client de carte, et certaines sont effectuées par l’adaptateur.  
  
1.  Les appels du système SAP dans l’adaptateur pour demander si un TID a déjà été utilisé. L’adaptateur renvoie la réponse appropriée au système SAP. Si le TID est nouveau, l’adaptateur crée une transaction validable. Cette opération permet de conserver le TID à la base de données TID de façon transactionnelle lorsque le programme SAP effectue une validation (COMMIT WORK). Il est également exposé au code d’application qui gère le trafic entrant tRFCs. En outre, l’adaptateur crée un GUID il associe le TID SAP.  
  
2.  Le système SAP envoie un ou plusieurs RFC transactionnelles à l’adaptateur. Pour chaque tRFC, l’adaptateur appelle l’opération tRFC approprié sur votre application. L’adaptateur transmet la transaction créée à l’étape 1 à votre application pour chaque opération. L’adaptateur transmet le GUID créé à l’étape 1 dans le message de demande pour l’opération.  
  
3.  Système SAP valide le LUW (COMMIT WORK). L’adaptateur tente de valider la transaction avec le TID SAP (créé à l’étape 1).  
  
    1.  Si la transaction est abandonnée (par votre application) au cours d’un des appels à l’étape 2, une erreur se produit lorsque l’adaptateur tente de valider la transaction. L’erreur est retournée à SAP. Passez à l’étape 4.  
  
    2.  Si la validation est réussie, le TID est désormais dans la base de données TID. Passez à l’étape 5.  
  
4.  Si une erreur s’est produite dans l’étape 3, ou si SAP est restaurée LUW (RESTART_OF_BACKGROUNDTASK) au lieu de sa validation, l’adaptateur annule la transaction. Dans ce cas le TID n’est jamais enregistré sur la base de données TID.  
  
5.  Le système SAP confirme le TID. L’adaptateur supprime le TID de la base de données TID (en supposant que l’étape 3 s’est terminée avec succès et le TID existe dans la base de données TID.  
  
> [!NOTE]
>  Si une erreur se produit, essayez de vous connecter à la base de données TID pendant une opération de serveur tRFC, un code d’erreur indiquant que l’appel entrant à partir de SAP n'a pas été traitée par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est retournée à SAP.  
  
### <a name="receiving-idocs-as-a-trfc-server"></a>Recevoir des IDOC comme serveur tRFC  
 Vous utilisez la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme un serveur RFC ou un serveur tRFC pour recevoir des IDOC à partir du système SAP. Dans les deux cas, vous devez définir le **ReceiveIdocFormat** liaison de propriété pour spécifier le format dans lequel l’adaptateur doit émettre les données IDOC à votre application. Pour plus d’informations sur la réception IDOC avec l’adaptateur, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md). Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## <a name="special-trfc-operations"></a>Opérations tRFC spécial  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut également effectuer certaines opérations tRFC spéciale sur le système SAP. Une telle opération est RfcConfirmTransID.  
  
-   **RfcConfirmTransID.** Vous appelez cette opération sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour confirmer les appels tRFC effectués sur le serveur SAP. RfcConfirmTransID peut être nécessaire dans les scénarios où l’adaptateur est utilisé pour envoyer l’IDOC au serveur SAP comme un tRFC. L’opération n’est disponible sous la **TRFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 Pour plus d’informations sur la structure de message et l’action SOAP pour l’opération RfcConfirmTransID, consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)