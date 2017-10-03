---
title: "Le fichier de Configuration XML de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, mqsconfigwiz
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], mqsconfigwiz
- mqsconfigwiz [MQSeries adapters]
ms.assetid: 5f19e55c-0f2c-46d7-bb5d-1eb147c296b3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0356c69b90f0dcfd5fc636b302a97b2de5674b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-configuration-file-for-the-mqseries-adapter"></a><span data-ttu-id="2f8e0-102">Fichier de Configuration XML de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="2f8e0-102">XML Configuration File for the MQSeries Adapter</span></span>
<span data-ttu-id="2f8e0-103">Le fichier de configuration XML lu par **mqsconfigwiz** contient les mêmes informations qu’un utilisateur entre lors de l’utilisation de la version Windows de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="2f8e0-103">The XML configuration file read by **mqsconfigwiz** contains the same information a user enters when using the Windows version of the wizard.</span></span> <span data-ttu-id="2f8e0-104">Ces informations incluent l'identité de l'application, les ID utilisateur et mot de passe le cas échéant, le nom du rôle et la liste des utilisateurs membres de ce rôle.</span><span class="sxs-lookup"><span data-stu-id="2f8e0-104">This information includes the application identity and the user ID and password if required, the role name, and a list of users who are part of that role.</span></span>  
  
 <span data-ttu-id="2f8e0-105">Voici un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="2f8e0-105">An example of the file might appear as follows:</span></span>  
  
```  
<MQSeriesConfig>  
    <AppIdentity>thisuser</AppIdentity>  
    <userid>domain\username</userid>  
    <password>Bippity.Boppity</password>  
    <rolename>CreatorOwner</rolename>  
    <userlist>  
        <username>domain\user1</username>  
        <username>domain\user2</username>  
    </userlist>  
</MQSeriesConfig>  
```  
  
 <span data-ttu-id="2f8e0-106">Vous pouvez utiliser **thisuser**, **InteractiveUser**, **LocalService**, ou **NetworkService** comme valeurs pour **AppIdentity** .</span><span class="sxs-lookup"><span data-stu-id="2f8e0-106">You can use **thisuser**, **InteractiveUser**, **LocalService**, or **NetworkService** as values for **AppIdentity**.</span></span> <span data-ttu-id="2f8e0-107">Utilisez le **userid** et **mot de passe** éléments uniquement avec **thisuser**.</span><span class="sxs-lookup"><span data-stu-id="2f8e0-107">Use the **userid** and **password** elements only with **thisuser**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8e0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8e0-108">See Also</span></span>  
 [<span data-ttu-id="2f8e0-109">Configuration silencieuse de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="2f8e0-109">Silent Configuration of the MQSeries Adapter</span></span>](../core/silent-configuration-of-the-mqseries-adapter.md)