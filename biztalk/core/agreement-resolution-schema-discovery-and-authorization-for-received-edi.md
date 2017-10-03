---
title: "Résolution de l’accord, détection de schéma et l’autorisation des Messages EDI reçus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 503e307c-4cb0-49b5-8751-82dcea203151
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5f7fd9b022daf2d123de1c971797b53df202d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-schema-discovery-and-authorization-for-received-edi-messages"></a>Résolution de l'accord, détection du schéma et autorisation des messages EDI reçus
Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message EDI, le pipeline de réception EDI effectue une recherche d'accord de partenariat commercial, une détection de schéma et des processus d'autorisation pour déterminer comment traiter le message.  
  
## <a name="agreement-resolution"></a>Résolution de l'accord  
 Le pipeline de réception EDI effectue une résolution d'accord de partenariat commercial par le biais d'une série d'étapes pour déterminer s'il existe une correspondance entre les champs d'en-tête dans le message et les propriétés dans la définition de l'accord. Une fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a déterminé l'accord, il identifie le schéma de document qui s'applique à l'échange (voir ci-après). Il utilise les propriétés associées à l'accord correspondant et le schéma pertinent pour valider et traiter le message reçu.  
  
 Pour effectuer la résolution de l'accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] procède comme suit :  
  
1.  Résoudre l'accord en mettant en correspondance les qualificateurs et identificateurs du récepteur et de l'expéditeur présents dans l'en-tête de l'échange avec ceux présents dans les propriétés d'un accord.  
  
2.  Si l'étape 1 échoue, résoudre l'accord en mettant en correspondance uniquement les qualificateur et identificateur de l'expéditeur présents dans l'en-tête de l'échange avec ceux présents dans les propriétés d'un accord. Par ailleurs, comme l'étape 1 n'a pas réussi, on peut supposer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] recevra le message. Par conséquent, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] essaie de mettre en correspondance les qualificateur et identificateur du récepteur avec :  
  
    -   les valeurs « BT » et « HostX12Recvr » (pour les messages X12) et  
  
    -   les valeurs « BT » et « HostEdifactRecvr » (pour les messages EDIFACT)  
  
    > [!IMPORTANT]
    >  -   **BizTalk Server 2013 R2, 2013 et 2010**: les champs de The ISA5, ISA6, ISA7, ISA8, UNB2.1, UNB2.2, UNB3.1 et UNB3.2 sont obligatoires dans les paramètres d’accord.  
    > -   **BizTalk Server 2009 et 2006 R2**: champs de The ISA7, ISA8, UNB3.1 et UNB3.2 ne sont pas obligatoires dans les paramètres de tiers. Si les champs sont vides, le moteur EDI fournit une résolution basée sur les valeurs de ISA5, ISA6, UNB2.1 et UNB2.2.  
    > -   Pour prendre en charge les résolutions allant de BizTalk Server 2009 et BizTalk Server 2006 R2 aux versions les plus récentes de BizTalk Server, des ID (HostX12Recvr et HostEdifactRecvr) et qualificateurs (BT) codés en dur sont introduits.  
    > -   Vos messages EDIFACT doivent suivre la [les directives UNECE](http://www.unece.org/tradewelcome/areas-of-work/un-centre-for-trade-facilitation-and-e-business-uncefact/outputs/standards/unedifact/tradeedifactrules.html) pour la syntaxe de message et les règles.  
  
3.  Si l'étape 2 échoue, utiliser les propriétés de l'accord de secours.  
  
 Dans la première étape, pour X12, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les valeurs suivantes pour la mise en correspondance :  
  
-   ISA05 (qualificateur de l'expéditeur)  
  
-   ISA06 (identificateur de l'expéditeur)  
  
-   ISA07 (qualificateur du récepteur)  
  
-   ISA08 (identificateur du récepteur)  
  
 Pour EDIFACT, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les valeurs suivantes pour la mise en correspondance :  
  
-   UNB2.1 (identificateur de l'expéditeur)  
  
-   UNB2.2 (qualificateur de l'expéditeur)  
  
-   UNB3.1 (identificateur du récepteur)  
  
-   UNB3.2 (qualificateur du récepteur)  
  
 Utilisé pour la correspondance des propriétés de l’accord sont définies dans le **identificateurs** page des onglets d’accord spécifique à la direction de la **propriétés de l’accord** boîte de dialogue.  
  
 Ces quatre propriétés côté envoi et côté réception identifient de manière unique l'accord de partenariat commercial. L'utilisation des quatre propriétés vous offre plus de souplesse dans le traitement côté réception. Par exemple, cette méthode de résolution d'accord peut vous permettre d'envoyer des accusés de réception à plusieurs tiers sans créer plusieurs ports d'envoi.  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas résoudre l'accord à l'aide des quatre qualificateurs et identificateurs de l'expéditeur et du récepteur, il tente de résoudre l'accord en utilisant simplement les qualificateur et identificateur de l'expéditeur. Pour X12, ces champs sont ISA05 et ISA06 ; pour EDIFACT, il s'agit de UNB2.1 et UNB2.2. Comme avec une correspondance de propriétés de l’expéditeur et récepteur, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] correspond aux valeurs dans l’en-tête d’échange de l’accord définies dans le **identificateurs** page d’onglets de l’accord spécifique à la direction de la **Propriétés de l’accord** boîte de dialogue. Si seul le qualificateur de l’expéditeur et l’identificateur sont utilisés pour résoudre l’accord, le qualificateur du récepteur et l’identificateur doivent être non définis dans l’onglet d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
 Si aucun accord n'est trouvé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l'accord de partenariat commercial de secours, à moins que les paramètres du port requièrent l'authentification. Si le paramètre de port requiert une authentification (si le paramètre **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** est sélectionné dans le **général** page de la **propriétés du Port de réception**), un accord est obligatoire pour chaque échange reçu par le port de réception. Alors, si l'accord n'est pas résolu par la mise en correspondance de l'en-tête de l'échange avec les propriétés de l'accord, l'utilisation des propriétés de l'accord de secours pour déterminer l'accord n'est pas autorisée. L'échange est traité comme si l'authentification avait échoué si aucun accord n'est trouvé, et est interrompu.  
  
> [!NOTE]
>  Un message du pipeline EDI est transmis à l'étape réussie de la résolution d'accord jusqu'à ce qu'il soit résolu et que l'accord soit activé dans l'étape. Par exemple, si le message est résolu dans la première étape de la résolution d'accord mais que l'accord est désactivé, le message est transmis à l'étape réussie à des fins de résolution.  
  
## <a name="schema-discovery"></a>Détection de schéma  
 Une fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a déterminé l'accord qui correspond au message, il doit déterminer le schéma à utiliser pour valider et traiter le message. Il utilise les propriétés identifiées dans le **paramètres d’hôte Local** page d’unidirectionnel (côté envoi) onglet d’accord de la **propriétés de l’accord** boîte de dialogue.  
  
 Pour déterminer le schéma, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit d'abord déterminer l'espace de noms de schéma. Le Désassembleur EDI utilise un espace de noms par défaut pour les schémas standard fournis avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou détermine l'espace de noms à utiliser pour un schéma personnalisé.  
  
 Le **paramètres d’hôte Local** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue vous permet de configurer une grille de valeurs d’un espace de noms personnalisé. Si aucune correspondance n’est trouvée dans la grille, le désassembleur EDI utilise l’espace de noms par défaut dans le **espace de noms cible** champ marqué pour la ligne par défaut.  
  
### <a name="x12-schema-discovery"></a>Détection de schéma X12  
 Pour les messages X12, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine un espace de noms personnalisé à l'aide de l'identificateur de l'expéditeur de l'application (GS02) et l'ID de document informatisé (ST01) à partir de l'en-tête de l'échange entrant. Il tente de trouver une correspondance entre ces valeurs et les valeurs des propriétés GS02 et ST01 dans les **personnaliser l’espace de noms cible** grille dans le **paramètres d’hôte Local** page (sous **Transaction Définissez les paramètres**) de l’onglet d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue. S’il trouve une correspondance, il utilisera l’espace de noms cible identifié dans la même ligne de la grille pour déterminer le schéma pour valider et traiter le message. Si l'espace de noms cible n'est pas déterminé, l'espace de noms cible par défaut est utilisé. Si aucun espace de noms n’est identifié dans le **espace de noms cible** champ marqué pour la ligne par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera l’espace de noms cible identifié dans les propriétés de l’accord de secours pour les messages encodés en X12, qui par défaut est `http://schemas.microsoft.com/BizTalk/Edi/X12/2006`.  
  
 Pour les échanges X12, après la détection de l'espace de noms cible, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le schéma à l'aide des informations suivantes :  
  
-   L'espace de noms cible venant d'être détecté.  
  
-   La version d'origine/version finale dans les cinq premiers caractères de ST03 (si GS07 == X - Accredited Standards Committee X12). Si ST03 n'est pas présent/valide ou ne donne pas la résolution de schéma, la version est déterminée par les cinq premiers caractères de GS08 ou de ISA12 (si GS07 != X).  
  
-   Le DocType dans ST01.  
  
 Le Désassembleur EDI concatène le type de codage, la version d'origine/version finale et le DocType pour déterminer le nom de schéma, par exemple, « X12_00401_864 ». Il concatène ensuite l'espace de noms cible avec le nom de schéma, par exemple, `http://schemas.microsoft.com/BizTalk/Edi/X12/2006/X12#X12_00401_864`.  
  
 Pour un échange HIPAA 837 entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge les trois schémas HIPAA 837 :  
  
|Schéma 837|Valeur GS08 dans la version 4010|Valeur GS08/ST03 dans la version 5010|  
|----------------|--------------------------------|--------------------------------------|  
|Claim-Dental_837D|004010X097A1|005010X224A1|  
|Claim-Institutional_837I|004010X096A1|005010X223A1|  
|Claim-Professional_837P|004010X098A1|005010X222|  
  
> [!NOTE]
>  Dans les versions HIPAA, pour le document informatisé 278 (Health Care Services Review), les paires de requête et réponse partagent la même valeur pour GS08 et ST01. En fonction des valeurs de déclenchement dans le champ BHT02, vous pouvez différencier une requête et une réponse 278 dans la version 5010 :  
>   
>  1.  L'une des valeurs 01, 13 et 36 dans BHT02 indique un Health Care Services Review Request.  
> 2.  11 dans BHT02 indique un Health Care Services Review Response.  
  
### <a name="edifact-schema-discovery"></a>Détection de schéma EDIFACT  
 Pour les messages EDIFACT, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine un espace de noms personnalisé à l'aide du type de message (UNH2.1), du numéro de version du message (UNH2.2), du numéro de version finale du message (UNH2.3), du code assigné (UNH2.5), de l'ID du groupe fonctionnel (UNG2.1) et du qualificateur de code de l'expéditeur de l'application (UNG2.2) à partir de l'en-tête de l'échange entrant. Il essaie alors de trouver une correspondance entre ces valeurs et les valeurs pour les propriétés UNH2.1, UNH2.2, UNH2.3, UNH2.5, UNG2.1 et UNG2.2 dans les **personnaliser l’espace de noms cible** grille (sous **paramètres des documents informatisés**) onglet d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue. S'il trouve une correspondance, il utilise l'espace de noms cible identifié dans la même ligne de la grille pour déterminer le schéma à utiliser pour valider et traiter le message. Si l'espace de noms cible n'est pas déterminé, l'espace de noms cible par défaut est utilisé. Si aucun espace de noms n’est identifié dans le **espace de noms cible** champ marqué pour la ligne par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera l’espace de noms cible identifié dans les propriétés de l’accord de secours pour les messages encodés en EDIFACT, qui est par défaut `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.  
  
 Pour les échanges EDIFACT, après la détection de l'espace de noms cible, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le schéma à l'aide des informations suivantes :  
  
-   L’espace de noms cible venant d’être détecté.  
  
-   Le numéro de version du message dans UNH2.2.  
  
-   Le numéro de version finale du message dans UNH2.3.  
  
-   Le type de message dans UNH2.1.  
  
-   Le code assigné dans UNH2.5.  
  
 Le Désassembleur EDI concatène le type de codage, la version, la version finale et le type de message pour déterminer le nom de schéma, par exemple, « EFACT_D94A_CONTEN ». Il concatène ensuite l'espace de noms cible avec le nom de schéma, par exemple, `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006/EFACT#EFACT_D94A_CONTEN`.  
  
 Si UNH2.5 est présent dans le message, le Désassembleur EDI tente d'abord de trouver un schéma correspondant à l'aide de la valeur de UNH2.5 dans le nom de schéma, par exemple « EFACT_D94A_CONTEN_TEST ». Si aucun schéma correspondant n'est trouvé, le Désassembleur EDI bascule pour trouver le schéma sans la valeur UNH2.5.  
  
## <a name="authorization"></a>Autorisation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie les valeurs des champs d'autorisation et de sécurité définis pour l'accord avec les champs dans le message. En cas d'incohérence, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interrompt l'échange. Pour les messages EDIFACT, ces champs sont Mot de passe du destinataire (UNB6.1 et UNB6.2). Pour les messages X12, ces champs sont Qualificateur et informations d'autorisation (ISA1-2) et Qualificateur et informations de sécurité (ISA3-4).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)