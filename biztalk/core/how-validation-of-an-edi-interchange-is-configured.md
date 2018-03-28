---
title: Configuration de la Validation d’un échange EDI | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e698b21-e234-4d7d-b101-742eff68155c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06485274a0053846c361d1aaab6707a073c16958
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-validation-of-an-edi-interchange-is-configured"></a>Configuration de la validation d'un échange EDI
Si le processus de recherche d'un accord identifie l'accord auquel un message entrant ou sortant correspond, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les propriétés d'accord (et non les propriétés de pipeline) pour déterminer la méthode de validation. Si aucun accord ne correspond à un échange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les propriétés d'accord de secours et certaines propriétés de pipeline dans le cadre de la validation.  
  
 Les tableaux suivants décrivent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine les validations à effectuer sur un échange EDI. Pour les colonnes Pipeline et Accord de secours du tableau, la valeur « Oui » désigne la configuration à utiliser lorsqu'aucun accord n'a été identifié.  
  
## <a name="general-information"></a>Informations générales  
  
|Validation|Configurée par le partenaire commercial|Configurée par le Pipeline<sup>*</sup>|Configurée par l'accord|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------------|----------------------------------------|-----------------------------|-----------------------------------------------|  
|Associations du port d'envoi|Oui|Non|Oui|non|  
|Certificats|Oui|Non|Non|non|  
|rapport d'état.|non|Non|Oui|Oui|  
  
> [!NOTE]
>  Il est déconseillé de définir les propriétés sur le pipeline, bien qu'elles soient disponibles via celui-ci.  
  
## <a name="agreement-for-outbound-interchangesbiztalk-receive-pipeline"></a>Accord relatif aux échanges sortants/au pipeline de réception BizTalk  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Informations de profil d’entreprise : contrat et Contact|Oui|-|-|  
  
 **Validation de X12 propriétés d’enveloppe**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Authentification/sécurité|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|ID de l'expéditeur|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|RepSeparator/<br />ISA11|Oui|Oui|non|  
|Doublon/validité dans ISA|Oui|Non|Oui|  
|Doublon/validité dans GS|Oui|Non|Oui|  
|Doublon/validité dans ST|Oui|Non|Oui|  
|NS/TS au niveau du groupe|Oui|Non|Oui|  
|Version d'origine/version finale|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
  
 **Validation des propriétés de l’enveloppe EDIFACT**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Mot de passe|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|SenderID|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|NS/TS au niveau du groupe|Oui|Non|Oui|  
|Version d'origine/version finale|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|Doublon/validité dans UNB|Oui|Non|Oui|  
|Doublon/validité dans UNG|Oui|Non|Oui|  
|Doublon/validité dans UNH|Oui|Non|Oui|  
|Délimiteurs UNA|non|Oui|non|  
  
 **Propriétés de l’accusé de réception générales**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Accusé de réception bidirectionnel|Oui|Oui|non|  
|Génération d'un accusé de réception fonctionnel|Oui|Non|Oui|  
|Accusé de réception de l'échange par lot|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|Contrôle de l'accusé de réception personnalisé|Oui|Non|Oui|  
|Génération d'un accusé de réception de l'échange|Oui|Non|Oui|  
|Accusé de réception de l'échange par lot|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|Contrôle de l'accusé de réception personnalisé|Oui|Non|Oui|  
|Création de rapports de contrôle|Oui|Non|Oui|  
  
 **Propriétés de validation sur la charge utile**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Routage|Oui|Oui|non|  
|Étendue|Oui|Oui|non|  
|Séparateurs de fin|Oui|Oui|non|  
|Génération de balises pour les séparateurs de fin|Oui|Oui|non|  
|Masquage de la sécurité/du mot de passe|Oui|Oui|non|  
|Conversion décimale|Oui|Oui|non|  
|Traitement par lot|-|-|-|  
|Conserver l'échange|Oui|Oui|non|  
  
> [!NOTE]
>  Il est déconseillé de définir les propriétés sur le pipeline, bien qu'elles soient disponibles via celui-ci.  
  
## <a name="agreement-for-inbound-interchangesbiztalk-send-pipeline"></a>Accord relatif aux échanges entrants/au pipeline d'envoi BizTalk  
 **X12 génération de l’enveloppe**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Segments ISA/GS/ST|Oui|Non|Oui|  
  
 **Génération de l’enveloppe EDIFACT**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Segments UNA/UNB/UNG/UNH|Oui|Non|Oui|  
|Délimiteurs UNA|Oui|Non|Oui|  
  
 **Paramètres de l’accusé de réception attendu**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Paramètre de l'accusé de réception Fn|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
  
 **Propriétés de validation sur la charge utile**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Routage|Oui|Oui|non|  
|Étendue|Oui|Oui|non|  
|Génération de séparateurs de fin|Oui|Oui|non|  
  
 **Création du lot**  
  
|Validation|Configurée par l'accord|Configurée par le Pipeline<sup>*</sup>|Configurée par les paramètres de l'accord de secours|  
|----------------|-----------------------------|----------------------------------------|-----------------------------------------------|  
|Critères de déclenchement|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|Plage|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
|Filtres|Oui|Disponible au niveau de l'accord uniquement|Disponible au niveau de l'accord uniquement|  
  
> [!NOTE]
>  Il est déconseillé de définir les propriétés sur le pipeline, bien qu'elles soient disponibles via celui-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)