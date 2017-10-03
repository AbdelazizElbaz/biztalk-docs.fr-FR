---
title: Bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agreements, 0A1 agreements
- loopbacks, running
- loopbacks, 0A1 agreements
- loopbacks, about loopbacks
- loopbacks, 0A1 messages
- agreements, loopback agreements
- messages, 0A1 messages
- loopbacks
- Loopback utility
- loopbacks, syntax
- 0A1 messages
- loopbacks, Loopback utility
- syntax [loopbacks]
- agreements, Loopback utility
ms.assetid: b4ebbdac-05be-4dfc-a133-6b752994e85a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346ed59bbf1666861a6a899c7cf7e4ca8646810a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loopback"></a>Bouclage
Vous utilisez l’utilitaire de bouclage pour générer automatiquement un accord de bouclage qui est une copie miroir d’un contrat d’origine à un partenaire. Vous pouvez ainsi effectuer des échanges de messages d'une organisation d'origine à un partenaire et d'un partenaire à une organisation d'origine sur un seul ordinateur. Vous pouvez utiliser cet utilitaire pour un scénario avec des messages de 0 a 1 ou dans un scénario sans les messages 0 a 1. Vous pouvez créer un accord de bouclage pour un contrat de message d’action (non-0 a 1) ou d’un accord 0 a 1.  
  
 Vous pouvez également utiliser l’utilitaire pour inscrire ou désinscrire une organisation d’origine pour un rôle expéditeur. Lorsque vous utilisez l’utilitaire pour activer une organisation d’origine, il crée deux ports d’envoi, \<Accueil >. Async et \<Accueil >. Synchronisation, que l’organisation utilise pour communiquer avec leurs partenaires.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*> \ programme Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\  
  
## <a name="running-loopback"></a>En cours d’exécution en boucle  
  
#### <a name="to-run-loopback"></a>Pour exécuter en boucle  
  
1.  Ouvrez une invite de commandes.  
  
2.  Déplacer vers \< *lecteur*> \ programme Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\\.  
  
3.  À l’invite de commandes, tapez **bouclage**, tapez les interrupteurs requis, puis appuyez sur ENTRÉE.  
  
## <a name="syntax-for-loopback"></a>Syntaxe de bouclage  
 Voici la syntaxe que vous utilisez pour démarrer cet utilitaire de ligne de commande :  
  
```  
Loopback [/enable|/disable <home_organization>] [/mirror|/unmirror <agreement_name>] [/NoF <0A1_agreement>]  
```  
  
## <a name="syntax-description"></a>Description de la syntaxe  
 Le tableau suivant décrit chaque partie de la syntaxe utilisée par l’utilitaire de bouclage.  
  
|**Syntaxe**|**Description**|  
|----------------|---------------------|  
|**Activer**|Inscrit l’organisation désignée dans < home_organization > pour un rôle expéditeur. Il crée deux ports d’envoi, \<Accueil >. Async et \<Accueil >. Synchronisation, que le partenaire utilise pour communiquer avec l’organisation d’origine.|  
|**désactiver**|Désinscrit l’organisation d’origine pour un rôle expéditeur.|  
|**home_organization**|Le partenaire à être inscrit ou désinscrit pour un rôle expéditeur.|  
|**mise en miroir**|Crée un accord de bouclage en fonction de l’accord désigné dans \< **agreement_name**>.|  
|**mettre fin au miroir**|Supprime l’accord de bouclage en fonction de l’accord désigné dans \< **agreement_name >**.|  
|**agreement_name**|L’accord en miroir ou de mettre fin au miroir dans le scénario de bouclage.|  
|**N**|Définit le **0 a 1 accord** propriété du contrat de message d’action mise en miroir par l’utilitaire de bouclage \<0A1_agreement >. A **/nde** commutateur ne peut être ajouté à une commande de bouclage qui contient également un **/miroir** basculer.|  
|**0A1_agreement**|Un accord 0 a 1 à utiliser par l’accord de mise en miroir du agreement_name. Ce contrat est généré par un accord de 0 a 1 répondeur de mise en miroir.|  
  
## <a name="remarks"></a>Notes  
 L’utilitaire de bouclage bascule les rôles de création de l’accord de bouclage. Si une organisation a été l’organisation d’origine dans le contrat d’origine, l’utilitaire permet de l’organisation partenaire dans l’accord de bouclage. De même, si une organisation a été l’organisation partenaire dans l’accord d’origine, l’utilitaire permet de l’organisation d’origine dans l’accord de bouclage. L’utilitaire bascule également le paramètre de la propriété de rôle de base. Si la propriété de rôle de base a été l’initiateur dans le contrat d’origine, l’utilitaire rend le répondeur et vice versa. Toutes les autres propriétés restent les mêmes.  
  
 L’utilitaire de bouclage des noms avec le même nom que le contrat d’origine, précédé par l’accord de bouclage » bouclage : ». Pour éviter toute confusion, n’affectez pas d’un accord en commençant par « bouclage ».  
  
 Si vous exécutez l’utilitaire sur un accord pour lequel vous avez déjà généré un accord de bouclage, l’utilitaire unmirrors l’accord de bouclage existant et crée un nouveau contrat de bouclage.  
  
 Vous avez besoin de l’utilitaire de bouclage, car vous ne pouvez pas créer un accord de mise en miroir dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. Vous ne pouvez pas créer un accord dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion pour lesquelles l’organisation d’origine, organisation partenaire et les propriétés de rôle de base sont inversées et tous les autres champs sont identiques aux champs d’un accord existant. De même, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge la modification de l’accord de bouclage directement dans la Console. Vous recevrez une erreur si vous essayez d’ouvrir un accord de bouclage dans la Console. Si vous devez apporter toute modification de l’accord de bouclage, modifiez l’accord d’origine, puis exécutez l’utilitaire de bouclage sur à nouveau pour régénérer l’accord de bouclage.  
  
> [!IMPORTANT]
>  Le scénario de bouclage ne prend pas en charge les contrats signés. Dans ce scénario, un message signé sera la validation échoue, car [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] vous permet de ne configurer qu’une seule partie avec un certificat de signature. Une organisation d’origine et une organisation partenaire ne pouvez pas utiliser le même certificat de signature. Il s’agit d’une limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] liés à l’identifiant de manière unique un tiers à l’aide d’un certificat de signature. Par conséquent, aucun tiers BizTalk ne peuvent partagent le même certificat.  
  
 Pour plus d’informations sur l’implémentation de bouclage, voir [didacticiel bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md).  
  
## <a name="using-loopback-with-0a1-agreements"></a>À l’aide de la boucle avec les contrats de 0 a 1  
 Vous pouvez configurer un scénario de bouclage pour générer des messages (notification d’échec) de 0 a 1. Pour ce faire, vous devez créer les accords de suivants pour l’organisation d’origine : un contrat de message d’action de demande, un accord de 0 a 1 initiateur et un contrat de 0 a 1 répondeur. Vous devez ensuite exécuter l’utilitaire de bouclage sur chacun de ces accords pour créer les accords de suivants pour l’organisation du partenaire : un contrat de message d’action de réponse, un accord de 0 a 1 initiateur et un contrat de 0 a 1 répondeur. Cela est nécessaire car vous ne pouvez pas utiliser le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion pour créer ces accords.  
  
 L’ensemble complet des accords doit inclure des contrats pour les messages suivants. À titre d’illustration, le message d’action est un 3 a 4 :  
  
-   Un accord de (message d’action) Home_to_Partner_3A4. Un accord pour lancer le message d’action PIP à partir de l’organisation d’origine vers l’organisation partenaire.  
  
-   Home_to_Partner_Initiator_0A1 des accords. Un accord pour lancer un PIP 0 a 1 à partir de l’organisation d’origine vers l’organisation partenaire.  
  
-   Home_to_Partner_Responder_0A1 des accords. Un accord pour recevoir un PIP 0 a 1 à partir de l’organisation partenaire de l’organisation d’accueil.  
  
-   Accord loopback:Home_to_Partner_3A4 (message de réponse). Un accord pour recevoir une 3 a 4 PIP à partir de l’organisation d’origine vers l’organisation partenaire.  
  
-   Loopback:Home_to_Partner_Responder_0A1 des accords. Un accord pour lancer un PIP 0 a 1 à partir de l’organisation partenaire de l’organisation d’accueil.  
  
-   Loopback:Home_to_Partner_Initiator_0A1. Un accord pour recevoir un PIP 0 a 1 à partir de l’organisation d’origine vers l’organisation partenaire.  
  
## <a name="creating-the-loopback-agreements-for-0a1-messages"></a>Création d’un accord de bouclage pour les Messages de 0 a 1  
 Pour créer l’ensemble des contrats, vous devez utiliser l’utilitaire de bouclage pour créer les contrats de message d’action et 0 a 1 sur le serveur partenaire. Les tableaux suivants indiquent les opérations de bouclage requises pour générer le partenaire de contrats de bouclage. À titre d’illustration, cette rubrique utilise un message de 3 a 4 dans les tables.  
  
|Étape|Contrats de base|  
|----------|---------------------|  
|1, 4|Home_to_Partner_3A4<br /><br /> Organisation d’accueil : accueil<br /><br /> Organisation du partenaire : partenaire<br /><br /> Rôle d’accueil : initiateur<br /><br /> Accord de 0 a 1 : Home_to_Partner_Initiator_0A1<br /><br /> Description : Accord pour lancer le PIP 3 a 4 à domicile à partenaire|  
|2|Home_to_Partner_Initiator_0A1<br /><br /> Accueil : accueil<br /><br /> Partenaire : partenaire<br /><br /> Rôle : initiateur<br /><br /> Description : Accord pour lancer le PIP 0 a 1 à domicile à partenaire|  
|3|Home_to_Partner_Responder_0A1<br /><br /> Accueil : accueil<br /><br /> Partenaire : partenaire<br /><br /> Rôle : répondeur<br /><br /> Description : Accord PIP 0 a 1 de réception du partenaire à l’accueil|  
  
|Étape|Accords de partenariat (mise en miroir à l’aide de Loopback.exe)|  
|----------|--------------------------------------------------------|  
|7|Loopback:Home_to_Partner_3A4<br /><br /> Accueil : partenaire<br /><br /> Partenaire : accueil<br /><br /> Rôle : répondeur<br /><br /> Accord de 0 a 1 : Loopback:Home_to_Partner_Responder_0A1<br /><br /> Description : Contrat de 3 a 4 PIP de réception à domicile au partenaire<br /><br /> Le bouclage de commande pour créer : bouclage /mirror Home_to_Partner_3A4 NoF Loopback:Home_to_Partner_Responder_0A1|  
|5|Loopback:Home_to_Partner_Responder_0A1<br /><br /> Accueil : partenaire<br /><br /> Partenaire : accueil<br /><br /> Rôle : initiateur<br /><br /> Description : Accord pour lancer le PIP 0 a 1 de partenaire à l’accueil<br /><br /> Le bouclage de commande pour créer : bouclage /mirror Home_to_Partner_Responder_0A1|  
|6|Loopback:Home_to_Partner_Initiator_0A1<br /><br /> Accueil : partenaire<br /><br /> Partenaire : accueil<br /><br /> Rôle : répondeur<br /><br /> Description : Accord pour recevoir des PIP 0 a 1 à domicile à partenaire<br /><br /> Le bouclage de commande pour créer : bouclage /mirror Home_to_Partner_Initiator_0A1|  
  
 Exécutez les commandes de bouclage dans ces tables dans le cadre de la procédure suivante.  
  
#### <a name="to-create-the-agreements-for-a-loopback-scenario-using-0a1-messages"></a>Pour créer des accords pour un scénario de bouclage à l’aide de messages de 0 a 1  
  
1.  Dans la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion, créer un accord pour le message d’action de demande être envoyés par l’organisation d’origine.  
  
2.  Créer un accord pour le message de 0 a 1 initiateur être envoyés par l’organisation d’origine et procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Mon organisation**|Valeur de l’organisation d’origine.|  
    |**Organisation du partenaire**|La valeur du partenaire.|  
    |**Rôle de base**|La valeur **PIP échec notifiant (initiateur)**.|  
  
3.  À l’aide de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion, créer un accord pour le message de 0 a 1 de répondeur à envoyer à l’organisation d’origine et procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Mon organisation**|Valeur de l’organisation d’origine.|  
    |**Organisation du partenaire**|La valeur du partenaire.|  
    |**Rôle de base**|La valeur **administrateur de rapports de défaillance (récepteur)**.|  
  
4.  À l’aide de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] set de la Console de gestion, le **0 a 1 accord** propriété pour demande message d’action accord l’organisation d’accueil au nom de l’initiateur 0 a 1 accord pour l’organisation d’origine.  
  
5.  À l’aide de l’utilitaire de bouclage, créez un accord pour le message de 0 a 1 initiateur être envoyés par l’organisation partenaire. Cela en mettant en miroir le répondeur accord 0 a 1 pour l’organisation d’origine. Cela crée un nouveau contrat 0 a 1 portant le nom **bouclage :\<nom de l’accord 0 a 1 >**. Le `My organization` est définie sur le serveur partenaire, le `Partner organization` est définie sur l’organisation d’origine et le `Home role` propriété est **PIP échec notifiant (initiateur)**.  
  
6.  À l’aide de l’utilitaire de bouclage, créez un accord pour le message de 0 a 1 répondeur pour l’organisation partenaire. Pour cela, vous la mise en miroir de l’accord d’initiateur 0 a 1 pour l’organisation d’origine. Cela crée un nouveau contrat 0 a 1 portant le nom **bouclage :\<nom de l’accord 0 a 1 >**. Le `My organization` est définie sur le serveur partenaire, le `Partner organization` est définie sur l’organisation d’origine et le `Home role` propriété est **administrateur de rapports de défaillance (récepteur)**.  
  
7.  À l’aide de l’utilitaire de bouclage, créez un accord pour le message d’action de réponse pour l’organisation partenaire. Dans la même commande, vous devez définir les propriétés de l’accord 0 a 1 de l’accord de 0 a 1 répondeur pour le partenaire. Pour cela, le contrat de message d’action de demande pour l’organisation d’origine de la mise en miroir, utilisez le **/nde** passer par le nom de contrat de 0 a 1 répondeur du partenaire. Cette opération crée un nouveau contrat de message d’action de réponse avec le nom **bouclage :\<nom de l’accord >**. Le `My organization` est définie sur le partenaire et la propriété d’accord de 0 a 1 est définie pour le contrat du partenaire répondeur 0 a 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [Didacticiel de bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)