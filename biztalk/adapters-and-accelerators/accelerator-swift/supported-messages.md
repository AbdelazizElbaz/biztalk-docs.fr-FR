---
title: Prise en charge des Messages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT messages, supported message types
ms.assetid: 9e059f86-05b1-4c6b-afa8-0ca969874a97
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb5f4f38b347f89a3272fd9476e6e3878e2701ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="supported-messages"></a>Messages pris en charge
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit une liste de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] et messages SWIFT. Les messages appartiennent à plusieurs catégories financières qui sont répertoriées ci-dessous.  
  
 Contenu de cette section :  
  
-   [Messages SWIFT - Microsoft](#fsa_intro_xtkj)  
  
-   [La catégorie 0 : Messages de système FIN](#fsa_intro_xcpk)  
  
-   [Catégorie 1 : Les paiements des clients et les vérifications](#fsa_intro_lxnf)  
  
-   [Catégorie 2 : Transferts d’établissement](#fsa_intro_fywg)  
  
-   [Catégorie 3 : Trésor marchés change, Money marchés et dérivés](#fsa_intro_qipa)  
  
-   [Catégorie 4 : Collections et les lettres de trésorerie](#fsa_intro_ruuc)  
  
-   [Catégorie 5 : Marchés de titres](#fsa_intro_iitn)  
  
-   [Catégorie 6 : Trésor marchés métaux précieux](#fsa_intro_bjez)  
  
-   [Catégorie 7 : Crédits documentaires et garanties](#fsa_intro_vhkw)  
  
-   [Catégorie 8 : Les chèques](#fsa_intro_qlwo)  
  
-   [Catégorie de 9 : Gestion des disponibilités et état du client](#fsa_intro_sptj)  
  
##  <a name="fsa_intro_xtkj"></a>Messages SWIFT - Microsoft  
 Le tableau suivant décrit les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] messages SWIFT pour les types de service amp et de contrôle de FIN.  
  
|type de message| Description|  
|------------------|-----------------|  
|**02**|Message de demande de connexion|  
|**03**|Sélectionnez la commande|  
|**05**|Quit (commande)|  
|**06**|Commande de déconnexion|  
|**12**|Demande de système supprimer l’Asie-Pacifique|  
|**13**|Confirmation de système abandon de l’Asie-Pacifique|  
|**14**|Demande système LT|  
|**15**|Confirmation de système de l’abandon LT d’initiée par l’utilisateur|  
|**21**|Accusé de réception de Message amp envoyé par un LT (accusé de réception/NON-RÉCEPTION)|  
|**21**|Accusé de réception d’un Message de l’amp reçu par un LT (accusé de réception/NON-RÉCEPTION)|  
|**21**|Accusé de réception d’un Message FIN envoyé par un LT (accusé de réception/NON-RÉCEPTION)|  
|**21**|Accusé de réception d’un Message FIN reçu par un LT (UAK/UNK)|  
|**22**|Accusé de réception positif connexion (LAK)|  
|**23**|Accusé de réception d’une requête Select (SAK)|  
|**25**|Quittez l’accusé de réception|  
|**26**|Accusé de réception de déconnexion|  
|**33**|Demande de l’utilisateur abandon de l’Asie-Pacifique|  
|**35**|Demande de l’utilisateur pour abandonner LT (abandon LT)|  
|**42**|Accusé de réception négatif connexion (LNK)|  
|**43**|Sélectionnez l’accusé de réception négatif (SNK)|  
  
##  <a name="fsa_intro_xcpk"></a>La catégorie 0 : Messages de système FIN  
 Le tableau suivant décrit la forme de messages catégorie 0 : financières Messages système, y compris l’utilisateur pour SWIFT et SWIFT à l’utilisateur.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 008**|Demande du système pour quitter|  
|**MT 009**|Demande de système de se déconnecter|  
|**MT 010**|Avertissement de non remise|  
|**MT 011**|Accusé de réception|  
|**MT 012**|Notification de l’expéditeur|  
|**MT 015**|NAK retardé|  
|**MT 019**|Abandon de Notification|  
|**MT 020**|Requête d’extraction (texte et l’historique)|  
|**MT 021**|Message récupéré (texte et l’historique)|  
|**MT 022**|Requête d’extraction (historique)|  
|**MT 023**|Message récupéré (historique)|  
|**MT 028**|Demande de Message état FIN|  
|**MT 029**|Rapport d’état FIN copie Message|  
|**MT 031**|Demande d’historique de session|  
|**MT 032**|Demande d’état de remise sous-ensemble|  
|**MT 035**|Demande de remise Instruction|  
|**MT 036**|Demande d’historique LT|  
|**MT 037**|Demande de statut de fuseau horaire|  
|**MT 041**|Sélectionnez la demande d’état de FIN|  
|**MT 042**|Limite de temps de demande d’une liste|  
|**MT 043**|Demande de liste non bancaire jours|  
|**MT 044**|Redéfinition de règles de rapport non remis|  
|**MT 045**|Vérification quotidienne heure de demande de modification|  
|**MT 046**|Demande de rapport de Message non remis|  
|**MT 047**|Demande de redéfinition des Instructions de remise|  
|**MT 048**|Demande de règles de rapport non remis|  
|**MT 049**|Requête de temps de rapport vérification quotidienne|  
|**MT 051**|Rapport historique de session|  
|**MT 052**|Rapport d’état de remise sous-ensemble|  
|**MT 055**|Rapport des Instructions|  
|**MT 056**|Rapport d’historique LT|  
|**MT 057**|Rapport d’état de fuseau horaire|  
|**MT 061**|Sélectionnez le rapport d’état de FIN|  
|**MT 062**|État de liste de temps d’arrêt|  
|**MT 063**|État de liste non bancaire jours|  
|**MT 064**|Rapport des modifications règles rapport non remis|  
|**MT 065**|Rapport des modifications de temps pour le rapport d’analyse quotidienne|  
|**MT 066**|Sollicitée de rapport sur les messages non remis|  
|**MT 067**|Rapport de redéfinition des Instructions|  
|**MT 068**|Règles de rapport non remis|  
|**MT 069**|Vérification de rapport temps rapport quotidien|  
|**MT 072**|Sélection du Mode de test|  
|**MT 073**|Exemple de demande de message|  
|**MT 074**|Requête de diffusion|  
|**MT 075**|Demande de certification|  
|**MT 076**|Erreur de certification|  
|**MT 077**|Autres critères de sélection de FIN|  
|**MT 081**|Rapport d’analyse quotidienne|  
|**MT 082**|Rapport de Message non remis à une heure fixe|  
|**MT 083**|Rapport de Message non livré au moment de la limite|  
|**MT 085**|Informations de remise ICC|  
|**MT 087**|Réponse de certification|  
|**MT 090**|Message de l’utilisateur pour SWIFT|  
|**MT 092**|Messages SWIFT à l’utilisateur|  
|**MT 094**|Broadcast|  
|**MT 096**|Copie FIN au Message de l’établissement centrale|  
|**MT 097**|Notification de FIN copie Message d’autorisation/refus|  
  
##  <a name="fsa_intro_lxnf"></a>Catégorie 1 : Les paiements des clients et les vérifications  
 Le tableau suivant décrit les messages à partir de la catégorie 1 : paiements et chèques.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 101**|Demande de transfert|  
|**MT 102**|Transfert de plusieurs clients|  
|**MT 102 +**|Transfert de plusieurs clients (STP)|  
|**MT 103**|Transfert de crédit client unique|  
|**MT 103 +**|Transfert de crédit client unique (STP)|  
|**MT 104**|Débit direct et demande de débit de transfert de Message|  
|**MT 105**|Enveloppe EDIFACT|  
|**MT 106**|Enveloppe EDIFACT|  
|**MT 107**|Message de prélèvement général|  
|**MT 110**|Conseils de chèques|  
|**MT 111**|Demande de paiement de mots vides de chèque|  
|**MT 112**|État d’une demande de paiement de mots vides de chèque|  
|**MT 121**|Transfert de fonds Interbank plusieurs (FINPAY EDIFACT)|  
|**MT 190**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 191**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 192**|Demande d’annulation|  
|**MT 195**|Requêtes|  
|**MT 196**|Réponses|  
|**MT 198**|Message propriétaire|  
|**MT 199**|Message au Format libre|  
  
##  <a name="fsa_intro_fywg"></a>Catégorie 2 : Transferts d’établissement  
 Le tableau suivant décrit les messages à partir de la catégorie 2 : les transferts Institution financière.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 200**|Transfert d’une Institution financière pour son propre compte|  
|**MT 201**|Plusieurs transfert Institution financière pour son propre compte|  
|**MT 202**|Transfert de l’établissement général|  
|**MT 203**|Transfert de plusieurs Institution financière général|  
|**MT 204**|Message de prélèvement marchés financiers|  
|**MT 205**|Institution financière transfère l’exécution|  
|**MT 206**|Message de troncation chèque|  
|**MT 207**|Demande de transfert d’une Institution financière|  
|**MT 210**|Avis de réception|  
|**MT 256**|Avis de Non paiement de chèques|  
|**MT 290**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 291**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 292**|Demande d’annulation|  
|**MT 293**|Message d’information Service|  
|**MT 295**|Requêtes|  
|**MT 296**|Réponses|  
|**MT 298**|Message propriétaire|  
|**MT 299**|Message au Format libre|  
  
##  <a name="fsa_intro_qipa"></a>Catégorie 3 : Trésor marchés change, Money marchés et dérivés  
 Le tableau suivant décrit les messages de la catégorie 3 : marchés Trésor change, Money marchés et dérivés.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 300**|Confirmation de change|  
|**MT 303**|Instruction d’Allocation Forex/devise Option|  
|**MT 304**|Conseils/Instruction d’un contrat de tiers|  
|**MT 305**|Confirmation de l’Option devise|  
|**MT 306**|Confirmation de l’Option devise|  
|**MT 307**|Conseils/Instruction d’un contrat de FX tiers|  
|**MT 308**|Instructions pour le règlement de chiffre d’affaires brut/Net des offres FX de tiers|  
|**MT 320**|Confirmation de prêt/dépôt fixe|  
|**MT 321**|Instructions pour régler un tiers prêt/dépôt|  
|**MT 330**|Appel/avis de Confirmation de prêt/dépôt|  
|**MT 340**|Confirmation de l’accord taux|  
|**MT 341**|Taux de transfert accord règlement Confirmation|  
|**MT 350**|Conseils d’intérêts prêt/dépôt|  
|**MT 360**|Confirmation de dérivés de taux d’intérêt seule devise|  
|**MT 361**|Cross-Confirmation de Swap de taux d’intérêt de devise|  
|**MT 362**|Taux d’intérêt de réinitialisation/conseils de paiement|  
|**MT 364**|Confirmation d’arrêt/Recouponing seule devise taux d’intérêt Swap|  
|**MT 365**|Cross-Confirmation d’arrêt/Recouponing devise taux d’intérêt Swap|  
|**MT 380**|Ordre de change|  
|**MT 381**|Confirmation de la commande change|  
|**MT 390**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 391**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 392**|Demande d’annulation|  
|**MT 395**|Requêtes|  
|**MT 396**|Réponses|  
|**MT 398**|Message propriétaire|  
|**MT 399**|Message au Format libre|  
  
##  <a name="fsa_intro_ruuc"></a>Catégorie 4 : Collections et les lettres de trésorerie  
 Le tableau suivant décrit les messages à partir de la catégorie 4 : Collections et les lettres de trésorerie.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 400**|Conseils de paiement|  
|**MT 405**|Nouvelle Collection|  
|**MT 410**|Acknowledgement|  
|**MT 412**|Conseils d’acceptation|  
|**MT 416**|Avis de Non-paiement/Non-acceptation|  
|**MT 420**|Tracer|  
|**MT 422**|Conseils de devenir et de demande pour obtenir des Instructions|  
|**MT 430**|Modification des Instructions|  
|**MT 450**|Avis de crédit de lettre de trésorerie|  
|**MT 455**|Conseils de réglage de trésorerie lettre crédit|  
|**MT 456**|Conseils de Dishonour|  
|**MT 490**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 491**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 492**|Demande d’annulation|  
|**MT 495**|Requêtes|  
|**MT 496**|Réponses|  
|**MT 498**|Message propriétaire|  
|**MT 499**|Message au Format libre|  
  
##  <a name="fsa_intro_iitn"></a>Catégorie 5 : Marchés de titres  
 Le tableau suivant décrit les messages à partir de la catégorie 5 : marchés de titres.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 500**|Instruction de Registre|  
|**MT 501**|Confirmation de l’inscription ou la Modification|  
|**MT 502**|Ordre d’acheter ou vendre|  
|**MT 503**|Revendication garantie|  
|**MT 504**|Proposition de garantie|  
|**MT 505**|Substitution de garantie|  
|**MT 506**|Documentation et l’instruction d’exposition|  
|**MT 507**|État de la garantie et les conseils de traitement|  
|**MT 508**|Conseils de intra-Position|  
|**MT 509**|Message d’état Commerce|  
|**MT 510**|État de l’inscription et les conseils de traitement|  
|**MT 513**|Conseils de client de l’exécution|  
|**MT 514**|Instruction d’Allocation de Commerce|  
|**MT 515**|Confirmation de client d’achat ou de vente|  
|**MT 516**|Confirmation de prêt de titres|  
|**MT 517**|Déclaration de Confirmation de Commerce|  
|**MT 518**|Les titres de marché côté Trade Confirmation|  
|**MT 519**|Modification des informations sur le Client|  
|**MT 524**|Instruction de intra-Position|  
|**MT 526**|Titres générales prêt/emprunt de Message|  
|**MT 527**|Instruction de garantie de tri tiers|  
|**MT 528**|Instruction d’etc. règlement du côté Client|  
|**MT 529**|Instruction de règlement de marché côté etc.|  
|**MT 530**|Commande de traitement de transaction|  
|**MT 535**|Déclaration d’exploitations|  
|**MT 536**|Instruction de Transactions|  
|**MT 537**|Instruction de Transactions en attente|  
|**MT 538**|Instruction d’avis de Position à l’intérieur de|  
|**MT 540**|Réception libre|  
|**MT 541**|Recevoir des paiements|  
|**MT 542**|Remettre libre|  
|**MT 543**|Remettre contre le paiement|  
|**MT 544**|Recevoir la Confirmation libre|  
|**MT 545**|Réception par rapport à la Confirmation de paiement|  
|**MT 546**|Fournir une Confirmation libre|  
|**MT 547**|Remettre par rapport à la Confirmation de paiement|  
|**MT 548**|Règlement et conseils de traitement|  
|**MT 549**|Demande de conseils de traitement des instructions|  
|**MT 558**|État de garantie de tri tiers et conseils de traitement|  
|**MT 559**|Revendication d’Agents payant|  
|**MT 564**|Notification d’Action d’entreprise|  
|**MT 565**|Instruction d’Action d’entreprise|  
|**MT 566**|Confirmation de l’Action d’entreprise|  
|**MT 567**|État de l’Action d’entreprise et des conseils de traitement|  
|**MT 568**|Action d’entreprise Narrative|  
|**MT 569**|Garantie de tri tiers et d’instruction d’exposition|  
|**MT 574**|(IRSLST) IRS 1441 ARN|  
|**MT 574**|(W8BENO) IRS 1441 ARN|  
|**MT 575**|Rapport d’activité combinée|  
|**MT 576**|Instruction de commandes en cours|  
|**MT 577**|Instruction de nombres|  
|**MT 578**|Règlement Allegement|  
|**MT 579**|Numéros de certificats|  
|**MT 581**|Message de l’ajustement de garantie|  
|**MT 582**|Demande de remboursement ou conseils|  
|**MT 584**|Instruction d’etc. en attente de transactions|  
|**MT 586**|Instruction de règlement Allegements|  
|**MT 587**|Instruction de réception dépositaire|  
|**MT 588**|Confirmation de réception dépositaire|  
|**MT 589**|État de réception dépositaire et des conseils de traitement|  
|**MT 590**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 591**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 592**|Messages SWIFT à l’utilisateur|  
|**MT 595**|Questions|  
|**MT 596**|Réponses|  
|**MT 598**|Message propriétaire|  
|**MT 599**|Message au Format libre|  
  
##  <a name="fsa_intro_bjez"></a>Catégorie 6 : Trésor marchés métaux précieux  
 Le tableau suivant décrit les messages à partir de la catégorie 6 : métaux précieux de marchés trésorerie, Trésor marchés Syndications et Messages courants de marchés de trésorerie.  
  
|type de message| Description|  
|------------------|-----------------|  
||**Trésorerie marchés métaux précieux**|  
|**MT 600**|Confirmation de Commerce complète|  
|**MT 601**|Confirmation de l’Option métaux précieux|  
|**MT 604**|Ordre de transfert/distribution de métaux précieux|  
|**MT 605**|Avis de métaux précieux à recevoir|  
|**MT 606**|Conseils de débit de métaux précieux|  
|**MT 607**|Avis de crédit métaux précieux|  
|**MT 608**|Instruction d’un compte complète|  
|**MT 609**|Instruction de contrats complètes|  
|**MT 620**|Confirmation de prêt de fixe complète/dépôt|  
||**Trésorerie marchés Syndications**|  
|**MT 643**|Avis de reprise ou de renouvellement|  
|**MT 644**|Conseils de vitesse et de la résolution de la quantité|  
|**MT 645**|Avis de frais d’échéance|  
|**MT 646**|Paiement du Principal et/ou d’intérêt|  
|**MT 649**|Message de fonctionnalité syndiqué général|  
||**Marchés Trésor - Messages courants**|  
|**MT 690**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 691**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 692**|Demande d’annulation|  
|**MT 695**|Requêtes|  
|**MT 696**|Réponses|  
|**MT 698**|Message propriétaire|  
|**MT 699**|Message au Format libre|  
  
##  <a name="fsa_intro_vhkw"></a>Catégorie 7 : Crédits documentaires et garanties  
 Le tableau suivant décrit les messages à partir de la catégorie 7 : documentaires crédits et garanties.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 700**|Problème de crédit documentaire|  
|**MT 701**|Problème de crédit documentaire|  
|**MT 705**|Avis préalable d’un crédit documentaire|  
|**MT 707**|Modification de crédit documentaire|  
|**MT 710**|Conseils de crédit documentaire banques tiers|  
|**MT 711**|Conseils de crédit documentaire banques tiers|  
|**MT 720**|Transfert de crédit documentaire|  
|**MT 721**|Transfert de crédit documentaire|  
|**MT 730**|Acknowledgement|  
|**MT 732**|Conseils de décharge électrostatique|  
|**MT 734**|Conseils de refus|  
|**MT 740**|Autorisation à rembourser|  
|**MT 742**|Demande de remboursement|  
|**MT 747**|Modification d’une autorisation à rembourser|  
|**MT 750**|Conseils de différence|  
|**MT 752**|Autorisation à payer, acceptez ou négocier|  
|**MT 754**|Conseils de paiement/acceptation/négociation|  
|**MT 756**|Conseils de remboursement ou de paiement|  
|**MT 760**|Garantie|  
|**MT 767**|Modification de la garantie|  
|**MT 768**|Accusé de réception d’un Message de garantie|  
|**MT 769**|Conseils de mise en production ou de réduction|  
|**MT 790**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 791**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 792**|Demande d’annulation|  
|**MT 795**|Requêtes|  
|**MT 796**|Réponses|  
|**MT 798**|Message propriétaire|  
|**MT 799**|Message au Format libre|  
  
##  <a name="fsa_intro_qlwo"></a>Catégorie 8 : Les chèques  
 Le tableau suivant décrit les messages à partir de la catégorie 8 : les chèques.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 800**|MT 800 T/C ventes et des conseils de règlement [unique]|  
|**MT 801**|MT 801 T/C plusieurs conseils d’achat|  
|**MT 802**|Conseils de règlement MT 802 T/C|  
|**MT 810**|Demande de remboursement MT 810 T/C|  
|**MT 812**|Autorisation de remboursement MT 812 T/C|  
|**MT 813**|Confirmation de restitution MT 813 T/C|  
|**MT 820**|MT 820 demande de Stock de T/C|  
|**MT 821**|Ajout de l’inventaire MT 821 T/C|  
|**MT 822**|Accusé de réception approbation 822 MT|  
|**MT 823**|Transfert de stock MT 823 T/C|  
|**MT 824**|Avis de Destruction/annulation inventaire MT 824 T/C|  
|**MT 890**|MT 890 conseils d’intérêt, les frais et les autres ajustements|  
|**MT 891**|MT 891 demande de paiement des frais, les intérêts et les autres frais|  
|**MT 892**|MT 892 demande l’annulation|  
|**MT 895**|MT 895 interroge|  
|**MT 896**|MT 896 des réponses|  
|**MT 898**|MT 898 Message propriétaire|  
|**MT 899**|Message de Format libre 899 MT|  
  
##  <a name="fsa_intro_sptj"></a>Catégorie de 9 : Gestion des disponibilités et état du client  
 Le tableau suivant décrit les messages à partir de la catégorie 9 : gestion des disponibilités et état du client.  
  
|type de message| Description|  
|------------------|-----------------|  
|**MT 900**|Confirmation de débit|  
|**MT 910**|Confirmation du crédit|  
|**MT 920**|Message de demande|  
|**MT 935**|Conseils de modification de taux|  
|**MT 940**|Message d’instruction de client|  
|**MT 941**|État du solde|  
|**MT 942**|Rapport des transactions intermédiaires|  
|**MT 950**|Message de l’instruction|  
|**MT 960**|Demande de Message du Service de lancement|  
|**MT 961**|Message de réponse de l’émission|  
|**MT 962**|Message de Service de clé|  
|**MT 963**|Message d’accusé de réception de clé|  
|**MT 964**|Message d'erreur|  
|**MT 965**|Erreur dans le Message de Service de clé|  
|**MT 966**|Interrompre le Message de Service|  
|**MT 967**|Message d’accusé de réception de l’arrêt|  
|**MT 970**|Instruction de compensation|  
|**MT 971**|Rapports de solde de compensation|  
|**MT 972**|Instruction intermédiaire de compensation|  
|**MT 973**|Message de demande de compensation|  
|**MT 985**|Requête d’état|  
|**MT 986**|Rapport d'état|  
|**MT 990**|Conseils de frais, d’intérêt et d’autres ajustements|  
|**MT 991**|Demande de paiement des frais, les intérêts et les autres frais|  
|**MT 992**|Demande d’annulation|  
|**MT 995**|Requêtes|  
|**MT 996**|Réponses|  
|**MT 998**|Message propriétaire|  
|**MT 999**|Message au Format libre|  
  
 Tous les messages suivent le *SWIFT normes version Guide 2008* spécifications. Pour plus d’informations sur la *Guide de mise en production de normes SWIFT*, consultez le site Web de SWIFT [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-messages.md)