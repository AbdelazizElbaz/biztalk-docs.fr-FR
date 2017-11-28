---
title: "Dépanner l’adaptateur JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5a55e52-039a-4aea-8251-b697fd061ddc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eac716a7567930509ebfd310cdaf9874286b349c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="2277f-102">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="2277f-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="2277f-103">Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="2277f-103">This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
## <a name="cannot-use-wildcards-in-send-port-properties"></a><span data-ttu-id="2277f-104">Impossible d’utiliser des caractères génériques dans les propriétés du port d’envoi</span><span class="sxs-lookup"><span data-stu-id="2277f-104">Cannot use wildcards in send port properties</span></span>  
 <span data-ttu-id="2277f-105">L'adaptateur pour JD Edwards EnterpriseOne ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés de port d'envoi suivants :</span><span class="sxs-lookup"><span data-stu-id="2277f-105">Adapter for JD Edwards Enterprise One does not support using wildcards in the following send port property fields:</span></span>  
  
-   <span data-ttu-id="2277f-106">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="2277f-106">Username</span></span>  
  
-   <span data-ttu-id="2277f-107">Environnement JDE</span><span class="sxs-lookup"><span data-stu-id="2277f-107">JDE Environment</span></span>  
  
-   <span data-ttu-id="2277f-108">Hôte</span><span class="sxs-lookup"><span data-stu-id="2277f-108">Host</span></span>  
  
-   <span data-ttu-id="2277f-109">Port</span><span class="sxs-lookup"><span data-stu-id="2277f-109">Port</span></span>  
  
-   <span data-ttu-id="2277f-110">Java_Home</span><span class="sxs-lookup"><span data-stu-id="2277f-110">Java_Home</span></span>  
  
-   <span data-ttu-id="2277f-111">Fichiers JAR JDE</span><span class="sxs-lookup"><span data-stu-id="2277f-111">JDE JAR Files</span></span>  
  
-   <span data-ttu-id="2277f-112">Nom du serveur de sécurité</span><span class="sxs-lookup"><span data-stu-id="2277f-112">Security Server Name</span></span>  
  
-   <span data-ttu-id="2277f-113">Connexion Nom de service</span><span class="sxs-lookup"><span data-stu-id="2277f-113">Service Name Connect</span></span>  
  
-   <span data-ttu-id="2277f-114">Nom de la source de données</span><span class="sxs-lookup"><span data-stu-id="2277f-114">Data Source Name</span></span>  
  
-   <span data-ttu-id="2277f-115">Propriétaire de la base de données</span><span class="sxs-lookup"><span data-stu-id="2277f-115">Database Owner</span></span>  
  
-   <span data-ttu-id="2277f-116">Nom du serveur de base de données</span><span class="sxs-lookup"><span data-stu-id="2277f-116">Database Server Name</span></span>  
  
-   <span data-ttu-id="2277f-117">Type de base de données</span><span class="sxs-lookup"><span data-stu-id="2277f-117">Database Type</span></span>  
  
-   <span data-ttu-id="2277f-118">Nom de la base de données physique</span><span class="sxs-lookup"><span data-stu-id="2277f-118">Physical Database Name</span></span>  
  
## <a name="connecting-to-oracle-database"></a><span data-ttu-id="2277f-119">Connexion à la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="2277f-119">Connecting to Oracle database</span></span>  
 <span data-ttu-id="2277f-120">Lorsque vous utilisez une base de données Oracle avec JD Edwards, vous devez modifier le fichier jdeinterop.ini.</span><span class="sxs-lookup"><span data-stu-id="2277f-120">When using Oracle database with JD Edwards you must modify the jdeinterop.ini file.</span></span> <span data-ttu-id="2277f-121">À l'aide de l'authentification unique, la section [JDBj-ORACLE] définit l'emplacement Oracle tnsnames. Le paramètre de base de données doit être utilisé, et le fichier SQLNET.ORA doit être présent sur l'ordinateur BizTalk Server (inclus avec le client Oracle).</span><span class="sxs-lookup"><span data-stu-id="2277f-121">Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).</span></span>  
  
 <span data-ttu-id="2277f-122">Ajoutez le code suivant au fichier jdeinterop.ini :</span><span class="sxs-lookup"><span data-stu-id="2277f-122">Add the following to the jdeinterop.ini file:</span></span>  
  
1.  <span data-ttu-id="2277f-123">Sous [JDBj-ORACLE] :</span><span class="sxs-lookup"><span data-stu-id="2277f-123">Under [JDBj-ORACLE]:</span></span>  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  <span data-ttu-id="2277f-124">Sous [JDBj-BOOTSTRAP données SOURCE] :</span><span class="sxs-lookup"><span data-stu-id="2277f-124">Under [JDBj-BOOTSTRAP DATA SOURCE]:</span></span>  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2277f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2277f-125">See Also</span></span>  
 <span data-ttu-id="2277f-126">[Ajouter l’adaptateur et créer les artefacts](../core/adding-biztalk-adapter-for-jd-edwards-enterpriseone.md) </span><span class="sxs-lookup"><span data-stu-id="2277f-126">[Add the adapter, and create the artifacts](../core/adding-biztalk-adapter-for-jd-edwards-enterpriseone.md) </span></span>  
 [<span data-ttu-id="2277f-127">Résolution des problèmes de JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="2277f-127">Troubleshooting JD Edwards EnterpriseOne</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)