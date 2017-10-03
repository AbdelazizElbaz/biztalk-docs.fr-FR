---
title: "Résolution des problèmes de la 1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, wildcard characters
- adapters [JD Edwards EnterpriseOne adapters], wildcard characters
- wildcard characters, JD Edwards EnterpriseOne adapters
ms.assetid: f5a55e52-039a-4aea-8251-b697fd061ddc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b77b42854a58d7fe8ffafd177e91f327a7f5e7e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="90b47-102">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="90b47-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="90b47-103">Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="90b47-103">This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
## <a name="cannot-use-wildcards-in-send-port-properties"></a><span data-ttu-id="90b47-104">Impossible d’utiliser des caractères génériques dans les propriétés du port d’envoi</span><span class="sxs-lookup"><span data-stu-id="90b47-104">Cannot use wildcards in send port properties</span></span>  
 <span data-ttu-id="90b47-105">L'adaptateur pour JD Edwards EnterpriseOne ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés de port d'envoi suivants :</span><span class="sxs-lookup"><span data-stu-id="90b47-105">Adapter for JD Edwards Enterprise One does not support using wildcards in the following send port property fields:</span></span>  
  
-   <span data-ttu-id="90b47-106">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="90b47-106">Username</span></span>  
  
-   <span data-ttu-id="90b47-107">Environnement JDE</span><span class="sxs-lookup"><span data-stu-id="90b47-107">JDE Environment</span></span>  
  
-   <span data-ttu-id="90b47-108">Hôte</span><span class="sxs-lookup"><span data-stu-id="90b47-108">Host</span></span>  
  
-   <span data-ttu-id="90b47-109">Port</span><span class="sxs-lookup"><span data-stu-id="90b47-109">Port</span></span>  
  
-   <span data-ttu-id="90b47-110">Java_Home</span><span class="sxs-lookup"><span data-stu-id="90b47-110">Java_Home</span></span>  
  
-   <span data-ttu-id="90b47-111">Fichiers JAR JDE</span><span class="sxs-lookup"><span data-stu-id="90b47-111">JDE JAR Files</span></span>  
  
-   <span data-ttu-id="90b47-112">Nom du serveur de sécurité</span><span class="sxs-lookup"><span data-stu-id="90b47-112">Security Server Name</span></span>  
  
-   <span data-ttu-id="90b47-113">Connexion Nom de service</span><span class="sxs-lookup"><span data-stu-id="90b47-113">Service Name Connect</span></span>  
  
-   <span data-ttu-id="90b47-114">Nom de la source de données</span><span class="sxs-lookup"><span data-stu-id="90b47-114">Data Source Name</span></span>  
  
-   <span data-ttu-id="90b47-115">Propriétaire de la base de données</span><span class="sxs-lookup"><span data-stu-id="90b47-115">Database Owner</span></span>  
  
-   <span data-ttu-id="90b47-116">Nom du serveur de base de données</span><span class="sxs-lookup"><span data-stu-id="90b47-116">Database Server Name</span></span>  
  
-   <span data-ttu-id="90b47-117">Type de base de données</span><span class="sxs-lookup"><span data-stu-id="90b47-117">Database Type</span></span>  
  
-   <span data-ttu-id="90b47-118">Nom de la base de données physique</span><span class="sxs-lookup"><span data-stu-id="90b47-118">Physical Database Name</span></span>  
  
## <a name="connecting-to-oracle-database"></a><span data-ttu-id="90b47-119">Connexion à la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="90b47-119">Connecting to Oracle database</span></span>  
 <span data-ttu-id="90b47-120">Lorsque vous utilisez une base de données Oracle avec JD Edwards, vous devez modifier le fichier jdeinterop.ini.</span><span class="sxs-lookup"><span data-stu-id="90b47-120">When using Oracle database with JD Edwards you must modify the jdeinterop.ini file.</span></span> <span data-ttu-id="90b47-121">À l'aide de l'authentification unique, la section [JDBj-ORACLE] définit l'emplacement Oracle tnsnames. Le paramètre de base de données doit être utilisé, et le fichier SQLNET.ORA doit être présent sur l'ordinateur BizTalk Server (inclus avec le client Oracle).</span><span class="sxs-lookup"><span data-stu-id="90b47-121">Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).</span></span>  
  
 <span data-ttu-id="90b47-122">Ajoutez le code suivant au fichier jdeinterop.ini :</span><span class="sxs-lookup"><span data-stu-id="90b47-122">Add the following to the jdeinterop.ini file:</span></span>  
  
1.  <span data-ttu-id="90b47-123">Sous [JDBj-ORACLE] :</span><span class="sxs-lookup"><span data-stu-id="90b47-123">Under [JDBj-ORACLE]:</span></span>  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  <span data-ttu-id="90b47-124">Sous [JDBj-BOOTSTRAP données SOURCE] :</span><span class="sxs-lookup"><span data-stu-id="90b47-124">Under [JDBj-BOOTSTRAP DATA SOURCE]:</span></span>  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="90b47-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90b47-125">See Also</span></span>  
 <span data-ttu-id="90b47-126">[Comment créer des Ports d’envoi pour JD Edwards EnterpriseOne](../core/how-to-create-send-ports-for-jd-edwards-enterpriseone.md) </span><span class="sxs-lookup"><span data-stu-id="90b47-126">[How to Create Send Ports for JD Edwards EnterpriseOne](../core/how-to-create-send-ports-for-jd-edwards-enterpriseone.md) </span></span>  
 [<span data-ttu-id="90b47-127">Résolution des problèmes de JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="90b47-127">Troubleshooting JD Edwards EnterpriseOne</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)