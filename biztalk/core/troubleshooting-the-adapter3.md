---
title: "Dépanner l’adaptateur JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dd6a951-f113-4f43-b43f-057a239d05c4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba2dd62e1d4b6dc0af1845d3129e69dbe582226
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="34180-102">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="34180-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="34180-103">Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="34180-103">This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="cannot-use-wildcards-in-send-and-receive-port-properties"></a><span data-ttu-id="34180-104">Impossible d'utiliser des caractères génériques dans les propriétés de port d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="34180-104">Cannot use wildcards in send and receive port properties</span></span>  
 <span data-ttu-id="34180-105">L'adaptateur pour JD Edwards OneWorld ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés suivants :</span><span class="sxs-lookup"><span data-stu-id="34180-105">Adapter for JD Edwards One World does not support using wildcards in the following property fields:</span></span>  
  
|<span data-ttu-id="34180-106">Propriété de port d'envoi</span><span class="sxs-lookup"><span data-stu-id="34180-106">Send Port Property</span></span>|<span data-ttu-id="34180-107">Propriété de port de réception</span><span class="sxs-lookup"><span data-stu-id="34180-107">Receive Port Property</span></span>|  
|------------------------|---------------------------|  
|<span data-ttu-id="34180-108">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="34180-108">Username</span></span>|<span data-ttu-id="34180-109">Chemin d'accès à l'événement</span><span class="sxs-lookup"><span data-stu-id="34180-109">Event File Path</span></span>|  
|<span data-ttu-id="34180-110">Environnement JDE</span><span class="sxs-lookup"><span data-stu-id="34180-110">JDE Environment</span></span>|<span data-ttu-id="34180-111">Préfixe du nom de la cible d'événement</span><span class="sxs-lookup"><span data-stu-id="34180-111">Event Target Name prefix</span></span>|  
|<span data-ttu-id="34180-112">Hôte</span><span class="sxs-lookup"><span data-stu-id="34180-112">Host</span></span>||  
|<span data-ttu-id="34180-113">Port</span><span class="sxs-lookup"><span data-stu-id="34180-113">Port</span></span>||  
|<span data-ttu-id="34180-114">Java_Home</span><span class="sxs-lookup"><span data-stu-id="34180-114">Java_Home</span></span>||  
|<span data-ttu-id="34180-115">Fichiers JAR JDE</span><span class="sxs-lookup"><span data-stu-id="34180-115">JDE JAR Files</span></span>||  
  
## <a name="connecting-to-oracle-database"></a><span data-ttu-id="34180-116">Connexion à la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="34180-116">Connecting to Oracle database</span></span>  
 <span data-ttu-id="34180-117">Lorsque vous utilisez une base de données Oracle avec JD Edwards, vous devez modifier le fichier jdeinterop.ini.</span><span class="sxs-lookup"><span data-stu-id="34180-117">When using Oracle database with JD Edwards you must modify the jdeinterop.ini file.</span></span> <span data-ttu-id="34180-118">À l'aide de l'authentification unique, la section [JDBj-ORACLE] définit l'emplacement Oracle tnsnames. Le paramètre de base de données doit être utilisé, et le fichier SQLNET.ORA doit être présent sur l'ordinateur BizTalk Server (inclus avec le client Oracle).</span><span class="sxs-lookup"><span data-stu-id="34180-118">Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).</span></span>  
  
 <span data-ttu-id="34180-119">Ajoutez le code suivant au fichier jdeinterop.ini :</span><span class="sxs-lookup"><span data-stu-id="34180-119">Add the following to the jdeinterop.ini file:</span></span>  
  
1.  <span data-ttu-id="34180-120">Sous [JDBj-ORACLE], tapez :</span><span class="sxs-lookup"><span data-stu-id="34180-120">Under [JDBj-ORACLE], type:</span></span>  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  <span data-ttu-id="34180-121">Sous [JDBj-BOOTSTRAP DATA SOURCE], tapez :</span><span class="sxs-lookup"><span data-stu-id="34180-121">Under [JDBj-BOOTSTRAP DATA SOURCE], type:</span></span>  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34180-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34180-122">See Also</span></span>  
 <span data-ttu-id="34180-123">[Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   </span><span class="sxs-lookup"><span data-stu-id="34180-123">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   </span></span>  
 [<span data-ttu-id="34180-124">Résoudre les problèmes de JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="34180-124">Troubleshoot JD Edwards OneWorld</span></span>](../core/troubleshooting-jd-edwards-oneworld.md)