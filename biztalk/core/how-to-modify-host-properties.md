---
title: "Comment modifier les propriétés de l’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5df9d7f-b6c2-4bb7-a845-284e6323e3d6
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a5dac64bb50cf84c0d14277687d1641b6fa536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-host-properties"></a>Mettre à jour les propriétés de l’hôte

## <a name="overview"></a>Vue d'ensemble
Vous pouvez utiliser la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour modifier les propriétés d’hôte suivant :  
  
-   **Groupe Windows :** membres du groupe Windows disposent des autorisations pour exécuter les instances de cet hôte par défaut. Lorsque vous devez choisir un groupe d'utilisateurs Windows pour un hôte BizTalk, il vous est recommandé de créer un groupe dédié à l'hôte. Si vous décidez d'utiliser un groupe existant, vérifiez que ce groupe ne dispose pas de plus de privilèges que nécessaire. Pour plus d’informations, consultez [contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md).  
  
    > [!NOTE]
    >  Si vous changez l'appartenance à un groupe d'un utilisateur actuellement connecté et que le groupe est également un membre du domaine, vous devez fermer la session et la rouvrir une fois les changements apportés. Autrement, l'accès sera refusé car l'appartenance au nouveau groupe ne sera pas reflétée par la connexion en cours.  
  
-   **Suivi de l’hôte :** au moins un ordinateur hôte du groupe doit effectuer le suivi des données d’intégrité et d’entreprise. Cette option indique si l'hôte charge le composant de suivi BizTalk pour traiter les données d'analyse du fonctionnement et d'entreprise.  
  
    > [!NOTE]
    >  Il est conseillé de créer au minimum une instance de l'hôte de suivi. S'il n'existe aucune instance d'hôte en cours d'exécution pour l'hôte de suivi, la base de données MessageBox continue à cumuler les données, entraînant par la suite une dégradation des performances.  
  
     L'hôte chargé du suivi dispose d'un accès en lecture/écriture aux tables de suivi de la base de données MessageBox ainsi que d'un accès à la base de données des suivis BizTalk. Par conséquent, les objets exécutés sur cet hôte bénéficient également d'un accès en lecture et en écriture à ces tables de base de données. Les hôtes qui n'assurent pas le suivi jouissent uniquement d'un accès en écriture aux tables de suivi de la base de données MessageBox et n'ont pas accès à la base de données des suivis BizTalk.  
  
    > [!NOTE]
    >  La sélection d'un hôte spécifique pour le suivi a des conséquences sur les performances des applications exécutées sur cet hôte. Vous pouvez donc décider de créer un hôte spécifique, dédié au suivi.  
  
-   **Approuvé par authentification :** vous pouvez spécifier que BizTalk Server approuve un hôte. BizTalk Server approuve **hôtes approuvés par authentification** pour placer l’expéditeur ID de sécurité (SSID) sur les messages que l’hôte approuvé en file d’attente qui correspondent à des utilisateurs autres que pour l’ordinateur hôte. Pour plus d’informations sur les hôtes approuvés par authentification, consultez [authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md).  
  
     Vous ne pouvez pas utiliser les mêmes comptes de service pour les instances d'hôtes approuvés et celles d'hôtes non approuvés. Pour modifier le paramètre d'approbation d'une instance d'hôte lorsque cette instance utilise un compte de service également associé à d'autres instances d'hôte, effectuez l'une des opérations suivantes :  
  
    -   Remplacez le compte de service de l'instance d'hôte dont vous voulez modifier les paramètres d'approbation par un nouveau compte de service.  
  
    -   Remplacez le compte de service de l'instance d'hôte par un compte de service existant, utilisé par d'autres instances d'hôte dont le paramètre d'approbation est identique.  
  
    -   Supprimez l'instance d'hôte et recréez-la avec un paramètre d'approbation et un compte de service différents.  
  
-   **Hôte par défaut dans le groupe :** il doit être un hôte par défaut dans le groupe à tout moment. Le processus d'inscription de l'orchestration utilise automatiquement l'hôte par défaut pour héberger l'orchestration, à moins que l'utilisateur n'ait sélectionné un hôte différent. Le premier hôte créé est marqué comme étant l'hôte par défaut. Pour plus d’informations sur l’hôte par défaut, consultez [hôtes](../core/hosts.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer des droits d'utilisateur suivants pour créer ou supprimer des hôtes et pour modifier leurs propriétés :  
  
-   Vous devez être membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur l’ajout d’utilisateurs au groupe Administrateurs de BizTalk Server, consultez [comment gérer le groupe d’administrateurs BizTalk Server](../core/how-to-manage-the-biztalk-server-administrators-group.md).  
  
-   Les droits suivants sont requis dans SQL Server :  
  
    -   Vous devez être soit un administrateur SQL Server, soit un membre des rôles de base de données SQL Server db_owner ou db_securityadmin dans la base de données des suivis BizTalk (BizTalk DTADb), dans les bases de données MessageBox (BizTalkMsgBoxDb) et dans la base de données d'importation principale BAM (BAMPrimaryImport).  
  
    -   Vous devez être membre du rôle SQL Server sysadmin sur tous les ordinateurs où résident des bases de données MessageBox, ou membre du rôle SQL Server db_owner ou db_ddladmin pour toutes les bases de données MessageBox.  
  
## <a name="steps"></a>Étapes  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **hôtes**.  
  
3.  Dans le volet de détails, cliquez avec le bouton droit sur l’hôte que vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’hôte** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Afficher le nom de l'hôte. Vous affectez un nom à l'hôte lorsque vous le créez.|  
    |**Type**|Afficher le type de l'hôte. Vous pouvez inscrire une orchestration auprès d'un hôte In-process qui peut héberger un gestionnaire d'envoi. Un hôte isolé s'exécute en dehors de l'installation BizTalk Server.|  
  
     **Options**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Autoriser le suivi de l’hôte**|Cette case à cocher doit être activée pour indiquer que l'hôte charge le composant de suivi BizTalk pour traiter l'analyse du fonctionnement et les données d'entreprise. Si vous activez cette case, l'hôte actuel disposera d'un accès en lecture et en écriture aux tables de suivi de la base de données MessageBox et à la base de données des suivis. Par conséquent, les objets exécutés sur cet hôte bénéficieront aussi d'un accès en lecture/écriture à ces bases de données. Si vous désactivez cette case, l'hôte disposera uniquement d'un accès en écriture aux tables de suivi de la base de données MessageBox et n'aura pas accès à la base de données des suivis BizTalk.|  
    |**Approuvé par authentification**|Cette case à cocher pour spécifier que BizTalk Server doit approuver cet ordinateur hôte.|  
    |**32 bits uniquement**|Cette case à cocher doit être activée pour que le processus de l'instance de l'hôte soit créé en tant que processus 32 bits sur les serveurs 32 bits et 64 bits. Si cette case est désactivée, ce processus sera créé en tant que processus 32 bits sur les serveurs 32 bits et en tant que processus 64 bits sur les serveurs 64 bits.<br /><br /> **Remarque** pour modifier un processus d’instance hôte 32 bits dans un processus d’instance hôte 64 bits, supprimez toutes les instances de l’hôte et désactivez la **32 bits seulement** case à cocher. Lorsque vous créez des instances d'hôte sur un serveur 64 bits, elles sont créées en tant que processus 64 bits.|  
    |**Transformer en hôte par défaut dans le groupe**|Cette case à cocher doit être activée pour identifier cet hôte en tant qu'hôte par défaut. Le processus d'inscription d'orchestration utilise automatiquement l'hôte par défaut pour héberger l'orchestration, sauf si vous sélectionnez explicitement un hôte différent. Si cette case est activée et indisponible, cet hôte est l'hôte par défaut.|  
    |**Groupe Windows**|Taper le groupe local ou le groupe de domaine de cet hôte. Les membres du groupe Windows disposeront des autorisations nécessaires pour exécuter des instances de cet hôte.|  
  
5.  Sur le **certificats** onglet, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Description**|Visualiser la description du certificat de déchiffrement affiché.|  
    |**Empreinte numérique**|Afficher l'empreinte du certificat de clé privée utilisée pour déchiffrer les messages entrants pour cet hôte. Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).|  
    |**Supprimer le certificat**|Supprimer de l'hôte le certificat de déchiffrement affiché.|  
    |**Parcourir**|Cliquez pour afficher les **sélectionner un certificat** boîte de dialogue, où vous sélectionnez le certificat de déchiffrement dans le magasin de certificats ordinateur Local ou d’autres personnes que vous souhaitez utiliser avec l’hôte.|  
  
## <a name="see-also"></a>Voir aussi  
-  [Optimisation de l’utilisation des ressources via la limitation de l’hôte](../core/optimizing-resource-usage-through-host-throttling.md)   
-  [Limitation des recommandations sur la conception](../core/throttling-design-recommendations.md)   
-  [Gestion des hôtes et des instances d’hôte BizTalk](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [Comment créer un nouvel hôte](../core/how-to-create-a-new-host.md)   
-  [Comment supprimer un ordinateur hôte](../core/how-to-delete-a-host.md)   
-  **MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]