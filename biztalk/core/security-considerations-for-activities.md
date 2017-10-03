---
title: "Considérations sur la sécurité pour les activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc49afd-a1c3-4ac7-8b89-11be667221e2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26ea453b24ac3e8df25e7a4da98f27731f3828be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-activities"></a>Considérations de sécurité pour les activités
Les rôles de sécurité utilisés lors de l'interception de l'adaptateur WCF sont les mêmes que ceux utilisés pour les autres solutions BAM. Les considérations supplémentaires pour intercepter l'adaptateur WCF impliquent la sélection de l'utilisateur et du rôle d'écriture d'événement appropriés à utiliser.  
  
 Lors de l'utilisation des services WCF et de l'adaptateur WCF, toutes les données BAM sont écrites dans la base de données Importation principale BAM par le rôle sélectionné.  
  
 Vous pouvez sélectionner la configuration de rôle utilisateur appropriée en évaluant votre scénario de solution :  
  
-   Si votre solution nécessite de nombreux nouveaux services qui sont suivis par de nombreuses activités différentes, et qui sont tous exécutés sous le même compte utilisateur, il est avantageux d'utiliser le super rôle BAM_EVENT_WRITER pour écrire les événements interceptés.  
  
    > [!NOTE]
    >  Les utilisateurs doivent être ajoutés au super rôle d'écriture d'événements BAM. Lors de l'ajout d'un utilisateur au super rôle il est important de se rappeler que l'utilisateur pourra alors écrire à toutes les activités dans le système.  
  
-   Si votre solution nécessite un contrôle plus important des événements écrits, alors vous devez utiliser des rôles spécifiques à l'activité.  
  
    > [!NOTE]
    >  Les utilisateurs doivent être ajoutés au rôle d'écriture d'événements spécifique à l'activité.  
  
 Pour plus d’informations sur la configuration des rôles d’enregistreur d’événements BAM, consultez [comment déterminer et définir des rôles d’écriture d’événements pour les activités](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).  
  
> [!IMPORTANT]
>  Vous devez être membre du groupe utilisateurs d’applications BizTalk.  
  
 Lors de la sélection du compte utilisateur à utiliser lors de la configuration de l'intercepteur WCF BAM pour la sécurité d'emprunt d'identité sous IIS vous devez prendre en compte les scénarios suivants :  
  
-   Auto-hébergé : Un exécutable en cours d’exécution sur votre ordinateur, qui contient le service WCF ouvert.  
  
-   Adaptateur WCF : Solutions créées à l’aide de la **Assistant Publication du Service WCF Biztalk**.  
  
-   Hébergé par IIS : une solution hébergée dans une application IIS à l’aide d’un Service WCF.  
  
 Utilisez le tableau suivant pour aider à identifier le compte à utiliser :  
  
|Type de solution|Compte à utiliser|  
|-------------------|--------------------|  
|Auto-hébergé|Le compte utilisé pour exécuter le fichier exécutable qui maintiendra le service ouvert.|  
|Adaptateur WCF|Utiliser l’identité du pool d’applications : il s’agit du pool d’applications associé au Vroot qui héberge l’emplacement de réception. Cette identité est créée automatiquement lorsque vous utilisez la **Assistant Publication du Service WCF BizTalk** pour publier le site. Vous pouvez considérer ceci comme un cas spécial de solution hébergée IIS.|  
|Hébergé IIS|L'identité de l'utilisateur AppPool exécutant le service WCF VRoot/Application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité pour les intercepteurs BAM](../core/security-considerations-for-bam-interceptors.md)