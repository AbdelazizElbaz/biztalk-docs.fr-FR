---
title: "Meilleures pratiques pour la sauvegarde et restauration des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, maintaining
- restoring, best practices
- best practices, backing up
- backing up, restoring
- backing up, best practices
- maintaining, best practices
- best practices, restoring
ms.assetid: 649ca56b-3cc1-49ad-9f74-ba1521e65ee1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2543f09c5118e58bd18ea2add113811fb733d884
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-backing-up-and-restoring-databases"></a><span data-ttu-id="44948-102">Méthodes conseillées pour la sauvegarde et la restauration des bases de données</span><span class="sxs-lookup"><span data-stu-id="44948-102">Best Practices for Backing Up and Restoring Databases</span></span>
<span data-ttu-id="44948-103">Consultez les meilleures pratiques suivantes relatives à la sauvegarde et à la restauration des bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="44948-103">Review the following best practices to help ensure that you can backup and restore your BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="44948-104">**Développer la sauvegarde et de restauration des stratégies et de les tester.**</span><span class="sxs-lookup"><span data-stu-id="44948-104">**Develop backup and restore strategies and test them.**</span></span>  
  
     <span data-ttu-id="44948-105">Une stratégie appropriée permet de restaurer rapidement des données perdues suite à une défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="44948-105">With a good plan, you can quickly recover your data if it is lost due to hardware failure.</span></span>  
  
-   <span data-ttu-id="44948-106">**Gérer l’espace disque et archivez les fichiers de sauvegarde précédentes.**</span><span class="sxs-lookup"><span data-stu-id="44948-106">**Manage disk space and archive previous backup files.**</span></span>  
  
     <span data-ttu-id="44948-107">Le travail de sauvegarde de BizTalk Server ne supprime pas les fichiers de sauvegarde obsolètes. Vous devez donc gérer ceux-ci afin de conserver de l'espace libre sur le disque.</span><span class="sxs-lookup"><span data-stu-id="44948-107">The Backup BizTalk Server job does not delete outdated backup files, so you need to manage those backup files to conserve disk space.</span></span> <span data-ttu-id="44948-108">Une fois que vous avez créé une sauvegarde complète de vos bases de données, vous devez déplacer les fichiers de sauvegarde obsolètes vers un périphérique de stockage d'archives pour libérer de l'espace sur le disque principal.</span><span class="sxs-lookup"><span data-stu-id="44948-108">After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.</span></span>  
  
-   <span data-ttu-id="44948-109">**Ne stockez pas de sauvegardes sur le même ordinateur ou le même disque que vous sauvegardez.**</span><span class="sxs-lookup"><span data-stu-id="44948-109">**Do not store backups on the same computer or disk that you are backing up.**</span></span>  
  
     <span data-ttu-id="44948-110">Vous devez spécifier un ordinateur ou un disque pour la sauvegarde différent de celui contenant les données d'origine.</span><span class="sxs-lookup"><span data-stu-id="44948-110">You should specify a computer or disk for your backup that is different from the computer with the original data.</span></span> <span data-ttu-id="44948-111">Sinon, vous risquez de perdre toutes vos données en cas de défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="44948-111">Otherwise, you will lose all of your data if the hardware fails.</span></span>  
  
-   <span data-ttu-id="44948-112">**Conserver des copies.**</span><span class="sxs-lookup"><span data-stu-id="44948-112">**Retain copies.**</span></span>  
  
     <span data-ttu-id="44948-113">Conservez au moins trois copies du support,</span><span class="sxs-lookup"><span data-stu-id="44948-113">Keep at least three copies of the media.</span></span> <span data-ttu-id="44948-114">dont une copie hors site au sein d'un environnement maîtrisé.</span><span class="sxs-lookup"><span data-stu-id="44948-114">Keep at least one copy off-site in a properly controlled environment.</span></span>  
  
-   <span data-ttu-id="44948-115">**Effectuer des tests de restauration.**</span><span class="sxs-lookup"><span data-stu-id="44948-115">**Perform trial restorations.**</span></span>  
  
     <span data-ttu-id="44948-116">Une fois par mois, réalisez une opération de restauration d'essai pour vérifier que vos fichiers ont été correctement sauvegardés.</span><span class="sxs-lookup"><span data-stu-id="44948-116">Perform a trial restoration at least once a month to verify that your files were properly backed up.</span></span> <span data-ttu-id="44948-117">Cette opération permet de détecter des problèmes matériels cachés qui ne sont pas mis au jour lors de la vérification du bon fonctionnement de votre logiciel.</span><span class="sxs-lookup"><span data-stu-id="44948-117">A trial restoration can uncover hardware problems that do not show up when you verify that your software is functioning properly.</span></span> <span data-ttu-id="44948-118">N'attendez pas une défaillance de votre disque dur pour découvrir si vous êtes en mesure de restaurer votre système et vos bases de données.</span><span class="sxs-lookup"><span data-stu-id="44948-118">Do not wait until your hard disk fails to see if you can restore your system and databases.</span></span>  
  
-   <span data-ttu-id="44948-119">**Sécurisation des appareils et des supports.**</span><span class="sxs-lookup"><span data-stu-id="44948-119">**Secure devices and media.**</span></span>  
  
     <span data-ttu-id="44948-120">Sécurisez à la fois le périphérique de stockage et le support de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="44948-120">Secure both the storage device and the backup media.</span></span> <span data-ttu-id="44948-121">Une personne peut très bien accéder à vos données à partir d'un support volé en les restaurant sur un autre serveur pour lequel il dispose des droits d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="44948-121">It is possible for someone to access the data from a stolen medium by restoring the data to another server for which they are an administrator.</span></span>  
  
-   <span data-ttu-id="44948-122">**Surveiller la sauvegarde et le processus de restauration.**</span><span class="sxs-lookup"><span data-stu-id="44948-122">**Monitor the backup and restore process.**</span></span>  
  
     <span data-ttu-id="44948-123">Pour garantir la réussite de ce processus, vous devez surveiller les travaux de l'Agent SQL Server qui permettent de sauvegarder et de restaurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="44948-123">To ensure that the backup and restore process was successful, you should monitor the SQL Server Agent jobs used to backup and restore BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44948-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44948-124">See Also</span></span>  
 [<span data-ttu-id="44948-125">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="44948-125">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)