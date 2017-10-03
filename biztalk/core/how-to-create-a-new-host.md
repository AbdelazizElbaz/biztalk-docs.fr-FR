---
title: "Créer un nouvel hôte | Documents Microsoft"
descriptions: Use BizTalk Administration to create a new host in BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 811e6e57-5c37-471a-aff4-5b2b68c367b1
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 700f0bb43a4f31b76819e7aca6fe5895cc2b6ab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-new-host"></a>Créer un nouvel hôte
Un hôte BizTalk est un conteneur logique d'éléments tels que des gestionnaires d'adaptateur, des emplacements de réception (y compris des pipelines) et des orchestrations. Afin de faciliter l'implémentation des mesures de sécurité et d'améliorer la gestion des hôtes, il est recommandé d'utiliser des hôtes distincts pour traiter, recevoir et envoyer des messages, ainsi que pour les éléments approuvés et non approuvés. Chaque serveur BizTalk ne peut contenir qu'une seule instance d'un hôte. Pour plus d’informations sur les ordinateurs hôtes, consultez [hôtes](../core/hosts.md).  
  
 Pour plus d’informations sur l’utilisation de Windows Management Instrumentation (WMI) pour créer un nouvel hôte, consultez **MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer des droits d'utilisateur suivants pour créer ou supprimer des hôtes et pour modifier leurs propriétés :  
  
-   Vous devez être membre du groupe d'administrateurs BizTalk Server.  
  
-   Les droits suivants sont requis dans SQL Server :  
  
    -   Vous devez être un administrateur SQL Server, ou un membre des rôles de base de données SQL Server db_owner ou db_securityadmin dans la base de données de suivi BizTalk (BizTalk DTADb), de bases de données MessageBox (BizTalkMsgBoxDb) et d’importation principale BAM (BAMPrimaryImport) base de données.  
  
    -   Vous devez être membre du rôle SQL Server sysadmin sur tous les ordinateurs où résident des bases de données MessageBox, ou membre du rôle SQL Server db_owner ou db_ddladmin pour toutes les bases de données MessageBox.  
  
## <a name="steps"></a>Étapes
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **hôtes**.  
  
3.  Dans le volet de détails, cliquez droit **hôtes**, cliquez sur **nouveau**, puis cliquez sur **hôte**.  
  
4.  Dans le **propriétés de l’hôte** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Afficher le nom de l'hôte. Vous affectez un nom à l'hôte lorsque vous le créez. Son nom ne doit pas comporter plus de 80 caractères.|  
    |**Type**|Afficher le type de l'hôte. Un hôte In-process peut héberger des orchestrations ainsi que certains gestionnaires d'envoi et de réception. Un hôte isolé est une limite de traitement en dehors de BizTalk Server requise par certains gestionnaires d'envoi et de réception. Vous pouvez inscrire une orchestration auprès d'un hôte In-process et un tel hôte peut héberger un gestionnaire d'envoi ou de réception.|  
  
     **Options**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Autoriser le suivi de l’hôte**|Cette case à cocher doit être activée pour indiquer que l'hôte traitera les données d'analyse du fonctionnement et d'entreprise. Si vous activez cette case, l'hôte actuel disposera d'autorisations en lecture/écriture sur les tables de suivi de la base de données MessageBox et sur celles de la base de données des suivis BizTalk. Par conséquent, les objets exécutés sur cet hôte bénéficieront aussi d'un accès en lecture/écriture à ces bases de données. Si vous désactivez cette case, l'hôte n'aura qu'un accès en écriture sur les tables de suivi de la base de données MessageBox ; il n'aura pas accès à la base de données des suivis BizTalk.|  
    |**Approuvé par authentification**|Cette case à cocher pour spécifier que BizTalk Server doit approuver cet ordinateur hôte.|  
    |**32 bits uniquement**|Activer cette case à cocher pour permettre au processus de l'instance d'hôte d'être créé en tant que processus 32 bits à la fois sur les serveurs 32 bits et 64 bits. Si cette case est désactivée, ce processus sera créé en tant que processus 32 bits sur les serveurs 32 bits et en tant que processus 64 bits sur les serveurs 64 bits.|  
    |**Transformer en hôte par défaut dans le groupe**|Cette case à cocher doit être activée pour identifier cet hôte en tant qu'hôte par défaut. Les orchestrations et ports créés utilisent automatiquement l'hôte par défaut pour héberger l'orchestration, sauf si vous sélectionnez explicitement un hôte différent. Si cette case est activée et indisponible, cet hôte est l'hôte par défaut.|  
    |**Groupe Windows**|Taper le groupe local ou le groupe de domaine de cet hôte. Les membres du groupe Windows disposeront des autorisations nécessaires pour exécuter des instances de cet hôte.|  
  
5.  Sur le **certificats** onglet, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom commun**|Visualiser la description du certificat de déchiffrement affiché.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisée pour déchiffrer les messages entrants pour cet hôte. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Supprimer de l'hôte le certificat de déchiffrement affiché.|  
    |**Parcourir**|Cliquez pour afficher les **sécurité Windows** boîte de dialogue, où vous sélectionnez le certificat de déchiffrement de l’utilisateur actuel ou le magasin personnel que vous souhaitez utiliser avec l’hôte.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md)   
 [Suppression d’un hôte](../core/how-to-delete-a-host.md)