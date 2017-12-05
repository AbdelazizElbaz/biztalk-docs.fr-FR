---
title: "Création ou modification d’un accord | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agreements, about agreements
- agreements, modifying
- agreements, creating
- agreements
- trading partners, agreements
- creating, agreements
- modifying, agreements
- agreements, trading partners
ms.assetid: 4bbe4b57-d6ec-4448-9c80-2aecd98e0dc7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ea033770504b0e0024a831e0ad8d8727603046e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-or-editing-an-agreement"></a>Création ou modification d’un accord
Cette rubrique décrit comment créer ou modifier un accord de partenariat commercial. Un accord de partenariat commercial configure la relation entre deux partenaires commerciaux, y compris son identité. le processus d’Interface partenaires (PIP) ; l’action, signaler et synchroniser les URL ; et les protocoles associés.  
  
 Un accord de partenariat commercial comprend les paramètres pour une configuration de processus, organisation d’origine, partenaires et contrat. Tous ces paramètres sont requis pour un accord. Vous pouvez créer une configuration de processus basée sur un PIP de RosettaNet ou un schéma personnalisé, mais vous devez créer la configuration. Vous devez également définir une organisation d’origine et une organisation partenaire. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]ne prend pas en charge l’échange de messages entre des parties inconnues.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]traite et valide un message basé sur l’ensemble de ces paramètres. Par exemple, pour un message CIDX, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] valide selon la version de Framework RNIF (RosettaNet Implementation) (1.1 uniquement), de l’accord 0 a 1 (pas 0 a 1 uniquement), et `Is Single Action` propriété (action unique uniquement). Un message CIDX validera uniquement si vous définissez la version RNIF à « 1.1 », l’accord 0 a 1 à « Aucune 0 a 1 » et le `Is Single Action` propriété `True`. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]valide également que toutes les propriétés de l’accord sont cohérentes avec les paramètres de profil de configuration de processus. Par exemple, il vérifie que vous avez défini le `Standard` propriété du profil à « CIDX » et que la propriété d’accord 0 a 1 de l’accord est définie à « Aucune 0 a 1 ».  
  
 Si vous modifiez un accord pendant un processus est actif, vous pouvez rencontrer des résultats imprévisibles. Les modifications apportées aux propriétés de l’accord seront applique dès que vous cliquez sur **appliquer** ou **OK** pour accepter les, mais vous ne pouvez pas prédire quelle étape d’un processus est en cours d’exécution. Après avoir modifié l’accord, toute nouvelle activité dans un processus en cours ou n’importe quel nouveau processus utilisera les propriétés modifiées. Toutefois, un processus en cours d’exécution lorsque vous modifiez l’accord ont déjà été utilisé les propriétés d’accord pour un message qu’il traite.  
  
 Après avoir créé un accord, vous devez l’activer pour activer les messages associés à l’accord pour être envoyé ou reçu. Vous pouvez également désactiver un accord afin d’éviter les messages associés à l’accord d’envoyé ou reçu. Vous devez désactiver un accord pour le modifier et puis le réactiver après la modification.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]enregistre ces informations dans la table TPAConfig dans la base de données BTARNCONFIG.  
  
 Les paramètres de l’accord de partenariat commercial sont comme indiqué dans le tableau suivant, organisé par onglet. Les paramètres par défaut sont les valeurs plus fréquemment utilisées. Procédures pour créer et modifier ces paramètres s’affichent après le tableau.  
  
|Onglet|Paramètre|Utilisation|  
|---------|-------------|-----------|  
|**Général**|**Nom**|Un nom unique pour le contrat, tel que Fabrikam_To_Contoso_3A2.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Configuration de processus**|L’identificateur pour le PIP.<br /><br /> Ce numéro identifie la configuration de processus qui est associée à ce contrat.<br /><br /> La valeur par défaut est le premier dans la liste des configurations de processus. La liste déroulante inclut toutes les configurations de processus entré précédemment.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Mon organisation**|L’organisation d’origine, sélectionnée dans la liste déroulante.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Organisation du partenaire**|L’organisation partenaire, sélectionnée dans la liste déroulante.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Description**|Description de l’accord de partenariat commercial.|  
|**Général**|**Version de RNIF**|La version de RNIF qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilisés pour les communications de l’accord.<br /><br /> Peut être **V01.10.00** ou **V02.00.01** (la valeur par défaut).<br /><br /> Doit être **V01.10.00** pour CIDX.|  
|**Général**|**Rôle de base**|Rôle de l’organisation d’origine.<br /><br /> Peut être le rôle de l’initiateur ou répondeur.|  
|**Général**|**Accord de 0 a 1**|Si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] retournera un message de Notification d’échec (PIP 0 a 1) lorsqu’une défaillance se produit.<br /><br /> Peut être **aucun 0 a 1** (la valeur par défaut) ou **0 a 1**.<br /><br /> Doit être **aucun 0 a 1** pour CIDX.|  
|**Général**|**Utilisation**|Indique le type de scénario qui utilise le contrat.<br /><br /> Peut être **Test** (la valeur par défaut) ou **Production**.|  
|**Général**<br /><br /> (**Adaptateur d’application** zone)|**Nom de l’assembly**|Le nom de fichier de la ApplicationAdapter que vous pouvez sélectionner le système de fichiers.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Général**<br /><br /> (**Module adaptateur**)|**Nom de classe**|Le nom de la classe qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilisera à partir de la ApplicationAdapter.<br /><br /> La valeur par défaut est \<aucun\>.|  
|**Général**<br /><br /> (**Zone de carte de validation**)|**Nom de l’assembly**|Le nom de fichier de la ValidationAdapter que vous pouvez sélectionner le système de fichiers. La valeur par défaut est une chaîne vide.|  
|**Général**<br /><br /> (**Zone de carte de validation**)|**Nom de classe**|Le nom de la classe qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilisera à partir de la ValidationAdapter.<br /><br /> La valeur par défaut est \<aucun\>.|  
|**Ports**|**URL d’action**|L’URL à laquelle l’organisation d’origine transmet un message d’action. Par exemple : http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> Il s’agit d’un champ obligatoire si les conditions suivantes sont réunies :<br /><br /> -La **est synchrone** paramètre de configuration de processus est `False`.<br /><br /> -La **est la seule Action** paramètre de configuration de processus est `True`.<br /><br /> -La **rôle d’accueil** paramètre d’accord est **initiateur**.<br /><br /> Cela est également un champ obligatoire si les conditions suivantes sont remplies (dans ce cas, le **URL de Signal** est également requis) :<br /><br /> -La **est synchrone** paramètre de configuration de processus est `False`.<br /><br /> -La **est la seule Action** paramètre de configuration de processus est `False`.<br /><br /> -Vous devez entrer un URI valide dans ce champ, qui commence par « http://domain » ou « https://domain ».|  
|**Ports**|**URL de signal**|L’URL à laquelle l’organisation d’origine transmet un message de signal. Par exemple : http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> Il s’agit d’un champ obligatoire si les conditions suivantes sont réunies :<br /><br /> -La **est synchrone** paramètre de configuration de processus est `False`.<br /><br /> -La **est la seule Action** paramètre de configuration de processus est `True`.<br /><br /> -La **rôle d’accueil** paramètre d’accord est **répondeur**.<br /><br /> Cela est également un champ obligatoire si les conditions suivantes sont remplies (dans ce cas, le **URL d’Action** est également requis) :<br /><br /> -La **est synchrone** paramètre de configuration de processus est `False`.<br /><br /> -La **est la seule Action** paramètre de configuration de processus est `False`.<br /><br /> Vous devez entrer un URI valide dans ce champ, qui commence par « http://domain » ou « https://domain ».|  
|**Ports**|**URL de synchronisation**|L’URL que l’organisation d’origine utilise pour établir une connexion via l’adaptateur HTTP. Par exemple : http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> Il s’agit d’un champ obligatoire si les conditions suivantes sont réunies :<br /><br /> -La **est synchrone** paramètre de configuration de processus est `True`.<br /><br /> -La **rôle d’accueil** paramètre d’accord est **initiateur**.<br /><br /> Vous devez entrer un URI valide dans ce champ, qui commence par « http://domain » ou « https://domain ».|  
|**Protocole**|**Méthode Digest**|Le protocole utilisé pour calculer le résumé des messages entrants à des fins de non-répudiation.<br /><br /> **En commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] et les versions plus récentes**, prise en charge SHA2 est automatiquement inclus. Les options sont : **MD5**, **SHA-1**, **SHA-256** (valeur par défaut), **SHA-384**, et **SHA-512**.<br /><br />Pour précédente [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] incluent des options de versions, **MD5** ou **SHA-1** (par défaut).<br /><br /> Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] réception pipeline reçoit et déchiffre un message, même si le protocole utilisé pour chiffrer le message et le **codage** paramètre sous cet onglet de l’accord ne correspondent pas. Par conséquent, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] reçoit des messages chiffrés dans RC2-40 ou 3DES.<br /><br /> Tous les messages sortants signés ont un condensat SHA-1.|  
|**Protocole**|**Encoder toutes les parties**|Indique si le système codera toutes les parties du message à parties multiples ensemble.<br /><br /> Peut être `True` ou `False` (la valeur par défaut).<br /><br /> Lorsque`True`, toutes les parties du message à parties multiples doit être encodés à l’aide de la méthode indiquée par le `Encoding` propriété.<br /><br /> Lorsque `False`, le système codera uniquement les pièces jointes à l’aide de la méthode indiquée par le `Encoding` propriété. (Les pièces jointes sont toujours codés par le pipeline d’envoi à l’aide de la méthode indiquée par le `Encoding` propriété.) Par défaut, lorsque vous définissez cette propriété sur `False`, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encode les autres parties du message (quatre parties dans RNIF 2.01, trois parties dans RNIF 1.1) au format quoted-printable.|  
|**Protocole**|**Encoding**|Le protocole utilisé pour coder toutes les parties (si le **encoder toutes les parties** zone est `True`) ou la pièce jointe (si le **encoder toutes les parties** zone est `False`).<br /><br /> Peut être **8 bits**, **base 64** (la valeur par défaut), ou **quoted printable**.|  
|**Protocole**|**Algorithme de chiffrement**|L’algorithme utilisé pour chiffrer les messages entrants et sortants.<br /><br /> **En commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] et les versions plus récentes**, prise en charge AES est automatiquement inclus. Les options sont **RC2-40**, **3DES**, **AES128** (valeur par défaut), **AES192**, et **AES256**. <br /><br />Pour précédente [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] incluent des options de versions, **RC2-40** (par défaut) ou **3DES**.<br /><br /> L’algorithme de chiffrement seulement prend effet que si vous avez défini le `Is Persistent Confidentiality Required` propriété **charge utile** ou **conteneur de charge utile** dans la configuration de processus correspondant.|  
|**Protocole**|**Direction de chiffrement**|Indique si le système chiffre le message entrant ou le message sortant ou les deux.<br /><br /> Peut être **entrant**, **sortant**, ou **entrantes et sortantes** (la valeur par défaut).<br /><br /> Le paramètre de direction de chiffrement ne prend effet que si vous avez défini le `Is Persistent Confidentiality Required` propriété **charge utile** ou **conteneur de charge utile** dans la configuration de processus correspondant.|  
|**Propriétés personnalisées**|**Nom**|Nom de la propriété personnalisée.<br /><br /> Vous pouvez définir des propriétés personnalisées sur une base par contrat. Si vous créez un nouveau processus privé personnalisé, vous pouvez utiliser ces propriétés personnalisées dans le traitement des contrats différents.<br /><br /> Vous pouvez utiliser la `RuntimeConfig.GetTPACustomConfigValue` méthode dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK pour récupérer des propriétés personnalisées à partir de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration.<br /><br /> Le `Name` propriété doit être unique et n’est pas vide.<br /><br /> Vous pouvez entrer les valeurs personnalisées suivantes :<br /><br /> - **AAR**. Il s’agit de la propriété personnalisée d’accusé de réception d’acceptation requis. Cela vaut uniquement pour RNIF 1.1. Affectez la valeur **false** (qui n’est pas sensible à la casse) pour n'exiger qu’un accusé de réception, pas un accusé de réception d’acceptation. Si **AAR** est une valeur autre que **false**, puis le processus public répondeur doit envoyer un accusé de réception d’acceptation et le processus public initiateur s’attend à recevoir un accusé de réception d’acceptation. Si AAR est définie sur false, les processus publics seront terminer après l’accusé de réception.<br /><br /> - **HPCC**. Voici le Code de classement accueil partenaire. Cela vaut uniquement pour RNIF 1.1. Cela vous permet de définir l’élément GlobalPartnerClassificationCode pour le partenaire d’accueil dans l’en-tête de service d’un message sortant à l’entrée dans la colonne valeur. Cette valeur remplace la propriété de classification accueil organisation dans la configuration de l’organisation d’origine. Utilisez cette propriété personnalisée lors de l’organisation d’origine peut avoir plusieurs classifications.<br /><br /> - **PPCC**. C’est le Code de Classification de profil de partenaire. Cela vaut uniquement pour RNIF 1.1. Cela vous permet de vous permet de définir l’élément GlobalPartnerClassificationCode pour le partenaire dans l’en-tête de service d’un message sortant à l’entrée dans la colonne valeur. Cette valeur substitue la propriété de classement de partenaire dans la configuration du partenaire. Utilisez cette propriété personnalisée lorsque le partenaire peut avoir plusieurs classifications.|  
|**Propriétés personnalisées**|**Valeur**|Valeur de la propriété personnalisée.|  
  
### <a name="to-create-a-trading-partner-agreement"></a>Pour créer un accord de partenariat commercial  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
4.  Dans la boîte de dialogue Propriétés de l’accord sur le **général**, **Ports**, **protocole**, et **propriétés personnalisées** onglets, entrez les valeurs pour les paramètres. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
5.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  BTARN n’accepte pas les messages relatifs à l’accord jusqu'à ce que vous activiez l’accord.  
  
6.  Cliquez sur le nom de l’accord dans le volet droit, puis cliquez sur **activer**.  
  
> [!NOTE]
>  Si vous avez déjà activé un accord, vous pouvez cliquez sur le nom de l’accord dans le volet droit, puis cliquez sur **Deactivate** afin d’éviter les messages associés à l’accord d’envoyé ou reçu.  
  
### <a name="to-edit-a-trading-partner-agreement"></a>Pour modifier un accord de partenariat commercial  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur le **accords** nœud.  
  
3.  Avec le bouton droit de l’accord que vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
4.  Dans le  **\<**  *nom de l’accord*  **\>**  boîte de dialogue des propriétés du **général** et  **Propriétés de contact** onglets, modifier les paramètres en fonction des besoins. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)   
 [Administration de la configuration de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)