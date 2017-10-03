---
title: "En-têtes SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT, headers
- headers [SWIFT]
ms.assetid: b599cca2-8ae6-42db-b3a2-712ba12c1017
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17003d43c5f8df74667f439ec83508820666fe9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-headers"></a>En-têtes SWIFT
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit le SWIFT schémas d’en-tête et le code de fin. A4SWIFT a déjà incorporé dans les schémas d’échange pour différents messages financières (FIN). Si vous souhaitez créer un SWIFT FIN format style message type personnalisé (par exemple, un message N98), vous pouvez incorporer les schémas d’en-tête et le code dans votre propre format.  
  
 Le schéma d’en-tête SWIFT (SWIFT Header.xsd) contient les formats pour les éléments suivants :  
  
-   En-tête de base  
  
-   En-tête de l’application (choix de l’entrée ou sortie)  
  
-   En-tête de l’utilisateur  
  
-   Délimiteur de début du bloc de texte  
  
 L’en-tête de base contient des informations sur la source du message. L’en-tête de l’Application contient des informations sur le type de message et la destination du message. La résolution du type de message par le désassembleur SWIFT dans un pipeline de réception est basée sur le contenu du champ dans l’en-tête d’Application approprié. L’en-tête de l’utilisateur est facultative et contient des instructions de traitement spécial.  
  
> [!NOTE]
>  Certains types de messages ont des formats variables en fonction du contenu du champ 119 dans l’en-tête de l’utilisateur. Il s’agit de « types de message double » dans A4SWIFT. Le désassembleur A4SWIFT utilise le type de message dans l’en-tête de l’Application conjointement avec la valeur du champ 119 pour sélectionner le schéma approprié pour une instance de message.  
  
 L’en-tête de l’utilisateur est facultatif et apparaît principalement pour une utilisation de la copie de la FIN. L’identificateur de Service dans le bloc 1 doit être « 01 ». Si l’en-tête est présent, au moins un des champs doit être présent. Toutefois, tous les champs sont facultatifs. Les champs dans l’en-tête de l’utilisateur suivent les mêmes règles que celles figurant dans la zone de texte du message.  
  
 Le tableau suivant répertorie tous les types de champ d’en-tête SWIFT.  
  
|Type de champ| Description|  
|----------------|-----------------|  
|**Identificateur de l’application (bloc 1)**|Désigne l’application qui a établi l’association, utilisée pour transmettre le message. Toujours utiliser **F** pour les messages FIN.|  
|**Bloquer l’identificateur (tous)**|Le premier caractère à l’intérieur de l’accolade ouvrante. L’identificateur de bloc est toujours suivi d’un signe deux-points.<br /><br /> **1** = en-tête de base<br /><br /> **2** = en-tête de l’application<br /><br /> **3** = en-tête de l’utilisateur<br /><br /> **4** = le texte du message<br /><br /> (Voir les valeurs ci-dessous pour le code de fin.)|  
|**Analyse de remise (bloc 2) (facultatif)**|Si la priorité est **U**, l’analyse de remise doit être :<br /><br /> **1** = avertissement de non remise<br /><br /> Ou<br /><br /> **3** = avertissement de non remise et de Notification de remise.<br /><br /> Si la priorité est **N**, l’analyse de remise doit être :<br /><br /> **2** = Notification de remise<br /><br /> Ou<br /><br /> Non inclus|  
|**Adresse de destination (bloc 2)**|L’adresse logique Terminal (LT) complète de la destination du message envoyé au réseau rapide.|  
|**Délimiteur de fin (bloque tout)**|Vous utilisez l’accolade fermante (**}**) pour le délimiteur de fin.|  
|**Identificateur d’entrée/sortie (bloc 2)**|**Je** = les messages envoyés à SWIFT.<br /><br /> **O** = les messages envoyés à partir de SWIFT.|  
|**Date (bloc 2) et l’heure d’entrée**|L’heure (HH) et les minutes (MM), suivie de l’année (aa), le mois (MM) et le jour (jj) sur lequel l’expéditeur a envoyé le message pour SWIFT. Date et heure d’entrée est toujours locale à l’expéditeur du message.|  
|**Adresse logique Terminal (LT) (bloc 1)**|L’adresse logique terminal de l’expéditeur pour les messages envoyés ou le récepteur de messages reçus à partir du réseau rapide.|  
|**Référence des messages d’entrée (MIR) (bloc 2)**|Date de que l’expéditeur a envoyé le message pour SWIFT écrite dans le format année (aa), month (MM) et jour (jj). Le MIR est toujours locale à l’expéditeur du message et est suivi par l’adresse LT complète de l’expéditeur du message et que la session et les séquence de l’expéditeur pour SWIFT.|  
|**Priorité du message (bloc 2)**|Priorité du message ; « S » pour les messages système (types 000 — 099) ; « U » pour Urgent ou « N » pour les messages à l’utilisateur (types 100-999).|  
|**Type de message (bloc 2)**|Trois chiffres FIN type de message, 000 à 999.|  
|**Période de l’obsolescence (bloc 2--facultatif)**|Valeur de 3 unités (15 minutes) pour la priorité vous et 20 unités de (100 minutes) pour N. la priorité par défaut (Valeurs par défaut toujours utilisés. Valide uniquement si l’analyse de la remise est présent.|  
|**Date de sortie (bloc 2)**|La date de sortie, locale pour le récepteur, écrites dans le format suivant : aammjj.|  
|**Heure de sortie (bloc 2)**|L’heure de sortie, local pour le récepteur, écrites dans le format suivant : HHMM.|  
|**Numéro de séquence (bloc 1)**|Pour tous les messages FIN avec l’identificateur Service **01** ou **05**, ce nombre est le numéro de séquence attendu approprié à la direction de la transmission.<br /><br /> Pour les messages FIN avec l’identificateur Service **21** ou **25**, le numéro de séquence est celle du message d’accusé de réception de service.|  
|**Identificateur de service (bloc 1)**|Un nombre à deux chiffres identifiant le type de message de service, en fonction de l’application de FIN. Pour tous les messages de types 000 à 999 de FIN, utilisez **01**. Pour tous les messages de types 02 à 43, utilisez leur type de message de service de deux chiffres.|  
|**Identificateur de session (bloc 1)**|Selon le cas, la session en cours d’application nombre basé sur la connexion.|  
|**Délimiteur de début (tous les blocs)**|L’accolade ouvrante : **{**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)