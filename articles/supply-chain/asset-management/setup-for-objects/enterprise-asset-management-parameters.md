---
# required metadata

title: Asset Management parameters
description: In Asset Management, general parameters relating to assets, work orders, and work order scheduling must be set up.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset Management parameters

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

In Asset Management, general parameters relating to assets, work orders, and work order scheduling must be set up. This topic explains how to set them up. Select **asset management** > **Setup** > **Asset management parameters** to open the form.

The **Create data wizard** button can be used to automatically create setup data for test or demo data purposes in a company in Dynamics 365 for Finance and Operations. Refer to the white paper "Set up Test Data in Asset Management" for information on how to use the wizard.

**Assets** link

- **Default functional location** is the standard functional location, which is automatically selected on assets when you create new assets.  
- In the **Standard calendar** field, select a calendar to be used for calculating asset KPIs, in case no resource is selected on an asset.  
- In the **View** field, select the standard view that is shown when you open the **Asset view** form (**Asset management** > **Common** > **Assets** > **Asset view**).
- **Default request type** is the standard maintenance request type, which is automatically selected when you create a new request.  
- If you want to create projects that relate to assets, project relations regarding selection of **Main project**, **Project hierarchy**, and the option to **Auto create projects** are set up in **Asset management parameters**.  
- In the **Work order project mask** field, you define the number of sub projects allowed for work orders and sub assets. A work order mask is used to define how many work orders can be created on an asset and used on the related work order job project. The work order mask is set up in the **Related Work order mask** field in **Asset management parameters** (**Asset management** > **Setup** > **Asset management parameters** > **Work orders**).  
>[!NOTE]
>The format for a related work order mask is a number of hash signs (#), depending on the maximum number of work orders you expect to create on an asset. Example: ## allows you to create up to 99 sub-projects.  
- Forecasts on job types are stored on the project selected in the **Forecast project** field. For each job type, a new activity is automatically created on the forecast project. Forecasts on the job type are then saved on the forecast project.  
- In the **Model** field, select the forecast model used on job type and work order forecasts.  


**Work orders** link

- **Default work order type** defines standard settings when creating a work order.  
- **Preventive work order type** defines the work order type used when creating work orders from maintenance plans. If this field is left blank, the work order type in the **Default work order type** field is used.  
- In the **Related work order mask** field, you define the maximum number of work orders that can be related to a work order. Example: Example: ## allows you to have up to 99 work orders related. If you define a mask as described here, related work orders will be numbered [work order ID of the work order to which a work order is related]-01, -02, -03, and so on. If you do not define a mask in this field, a related work order will get the next sequential work order ID.  
- Select "Yes" on the **Copy faults** toggle button if you want to automatically copy faults registered on work orders to related maintenance requests.  
- In the **Level** field, you define the functional location level that is automatically inserted on a work order if all related work order jobs refer to the same functional location. If the work order jobs do not all relate to the same functional location on the defined level, the **Functional location** field is left blank on the work order. Example: If you insert the number "1" in this field, that is the top level in a functional location structure. If you insert the number "0" in this field, you have not defined a specific functional location level, only that all work order jobs on a work order must be related to the same functional location for that functional location to be added to the work order.  
- Journals used when posting consumption on a work order can be selected on the **General** FastTab in the **Hour**, **Item**, and **Expense** fields.  
- In the **Product language source** field, select which language to use for product names in Asset management reports. You can select the language set up on the company account, or the language set up for the user currently logged in on Dynamics 365 for Finance and Operations.  
- Select "Yes" on the **Real time update** toggle button if you want to automatically update changes to job type defaults, maintenance plans, and maintenance rounds.
> - If you select "No", changes to job type defaults, maintenance plans, and maintenance rounds are not updated automatically in Asset Management  
> - Select "No" on the toggle button if you have large amounts of data being synchronized, for example, many assets or functional locations set up on maintenance plans or maintenance rounds, or a large number of maintenance plans or rounds.  
> - If you make changes to job type defaults or maintenance plans or maintenance rounds, and you have selected "No" to real time update, a warning may not be shown if the changes influence:
>   - functional locations set up on maintenance plans or rounds  
>   - objects set up on maintenance plans or rounds  
>   - maintenance plans setup  
>   - maintenance rounds setup  
- On the **Category** FastTab, default categories relating to consumption on work orders can be defined.  


**Work order scheduling** link

- **Schedule time fence** defines period in days, calculated from the expected start date of the work order, during which work order jobs are planned.  
- The **Master plan** relates to resources in the **Organization administration** module. If you select a master plan in this field, you will be able to see capacity reservations related to work orders in **Capacity reservations** (**Organization administration** > **Resources** > **Resources** > select resource > **Resource** tab > **Capacity reservations** button). If you leave this field blank, you will be able to see capacity load related to work orders in **Capacity load** (**Organization administration** \> **Resources** \> **Resources** \> select resource \> **Resource** tab \> **Capacity load** button).  

>[!NOTE]
>The selection regarding using a master plan or not in the **Asset management** module, and the related form used to get an overview of capacity reservations or capacity load is standard Dynamics 365 for Finance and Operations setup. Depending on your setup in the **Master plan** field, you will be able to access capacity information in either **Capacity reservations** or **Capacity load** in the **Organization administration** module. It is not possible to create a setup in which capacity reservations are shown in both views.  

The fields described in the bullet list below all relate to calculated rating scores, which are used to calculate work order priority during work order scheduling.

- **Priority** - a rating score calculated together with the rating score in the **Criticality** and **Start date** fields. The number in this field is divided by the number in the **Priority** field on a work order. Example: If the value "5.00" is inserted in this field, and a work order has priority "20", the rating score for priority is 0.25.  
- **Criticality** - a rating score calculated together with the rating score in the **Priority** and **Start date** fields. The number in this field is multiplied by the number in the **Criticality** field on a work order. Example: If the value "10.00" is inserted in this field, and a work order has criticality "5", the rating score for criticality is 50.  
- **Start date** - a rating score calculated together with the rating score in the **Priority** and **Criticality** fields. This field indicates daily score as a negative value and is compared to the **Expected start** field on a work order. Example: If the value "10.00" is inserted in this field, and the expected start date of a work order is three days from now, the rating result is minus 30.00. Adding the results of 0.25 and 50 from the examples in the **Priority** and **Criticality** fields described above provides a total of plus 20.25. That number is compared to all other work order rating scores during work order scheduling, and the highest rating scores are then planned first.  
- **Responsible worker** - a rating score calculated together with the **Responsible worker group**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. If the value "50.00" is inserted in this field, and a responsible worker has been selected on a work order, the worker gets 50 points in the overall worker calculation during work order scheduling.  
- **Responsible worker group** - a rating score calculated together with the **Responsible worker**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. If the value "50.00" is inserted in this field, and a responsible worker has been selected on a work order, the worker gets 50 points in the overall worker calculation during work order scheduling.  
- The **Limit to responsible** Yes/No toggle button limits the number of workers available for work order scheduling. Select "No" if you want to calculate a score for all workers, regardless that they are set up as responsible workers or part of a responsible worker group. Select "Yes" if you want to calculate a score for workers who are set up as responsible worker on the work order, and/or included in a responsible worker group selected on the work order.  
- **Preferred worker** - a rating score calculated together with the **Responsible worker**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. The four rating scores are calculated and added together to provide a score used for selecting which worker should be assigned to which work order during work order scheduling. If the value "10.00" is inserted in this field, and a worker has been selected as preferred worker on a work order, that worker gets 10 points in the overall worker calculation during work order scheduling.  
- **Preferred worker group** - a rating score calculated together with the **Responsible worker**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. If the value "10.00" is inserted in this field, and a worker has been assigned to a preferred worker group selected on a work order, that worker gets 10 points in the overall worker calculation during work order scheduling.  
- The **Limit to preferred** Yes/No toggle button limits the number of workers available for work order scheduling. Select "No" if you want to calculate a score for all workers, whether or not they are set up as preferred workers or part of a preferred worker group. Select "Yes" if you only want to calculate a score for workers who are set up as preferred workers, and/or included in a preferred worker group.  
- **Location** - rating score calculated together with the **Responsible worker**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. If the value "3,000.00" is inserted in this field, a worker gets 3,000 points in the calculation if the worker is located in the same factory or facility as the asset on which a job is to be scheduled.  

  - If your company uses functional locations, workers get full score if they are located on the functional location related to the asset. If the functional location of the asset has a parent asset, workers on that functional location get 1/2 score. If that location also has a parent, workers on that location get 1/3 score. If that location also has a parent, workers on that location get 1/4 score, and so on.  
  - If your company uses asset location, which we do not recommend, location, area, and zone are used to calculate location scores. Workers get full score if they are located in the location and area and zone related to the asset. If worker location only matches location and area, the rating score for the worker is 2/3 of the full score. If worker location only matches location, the rating score for the worker is 1/3 of the full score.  

- The **Limit to location** Yes/No toggle button limits the number of workers available for work order scheduling. Select "No" if you want to calculate a score for all workers across all functional locations. Select "Yes" if you only want to calculate a score for workers who are associated with the work order's functional location.

>[!NOTE]
>The three "Limit to..." toggle buttons are introduced to increase the speed of work order scheduling by limiting the number of scores calculated for workers.

**Worker's start date** - rating score calculated together with the **Responsible worker**, **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** rating score values. This field indicates daily score as a negative value and is compared to the **Expected start** field on a work order. If the value "10.00" is inserted in this field, and the expected start date of a work order is tomorrow, the rating result is minus 10.00.

  - Assuming that no responsible worker and responsible worker group have been selected on a work order to be scheduled - you add and subtract the rating score values in the examples in the **Preferred worker**, **Preferred worker group**, **Asset location**, and **Start date** fields above, you get a total of 3,010.00. This means a high score for the worker who is already selected as preferred worker as well as included in the preferred worker group on the work order, and the worker is also located in the same facility as the asset for which a job needs to be scheduled. All in all this means there is a good chance that the worker in question will be selected to complete the job during work order scheduling.  
  - If the value "0.00" is inserted in one of the eight fields above, that rating score will not be used during work order scheduling.  


**Document types** link

Select the document types that should be available for printing attachments related to a work order report. This is done by clicking on a document type in the **Available** section and clicking the ![forward arrow](media/15-setup-for-objects.png) button. If you want to remove a selected document type, select the document type in the **Selected** section and click the ![back arrow](media/16-setup-for-objects.png) button.



**Number sequences** link

Select the required number sequences in this section. There are two number sequences for assets: One for manually created assets, and one for assets created through pending assets.
