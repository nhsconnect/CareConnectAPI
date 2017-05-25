---
title: How To Write A Care Connect User Story
keywords: engage, explore, care connect process, process, introduction, user, story, tutorial, actor, primary, secondary, need, justification, acceptance, feature, epic
tags: [userstories]
sidebar: foundations_sidebar
permalink: howtouserstory.html
summary: "Industry suggests various techniques for the creation of user stories. Care Connect extends this slightly to help make the creation of user stories more relevant to the creation of system interfaces."
---

Given a clinical scenario, it is possible to derive several user stories that are suitable for mapping by considering the story from the perspective of the end users that will benefit from the final interface.
A user story in its simplest form is made up of three elements.

<table style="margin-left:auto;margin-right:auto;"><tr><td><b>Actor</b></td><td><b>Requirement</b></td><td><b>Justification</b></td></tr></table>

This simplicity makes the user story easy to understand and share across consumers with differing roles. To support Connect, this is supported with additional content such as the acceptance criteria (which is normally included as part of a user story) and secondary actors (which are not typically considered to be part of a user story).
## Actor
This end user is caller the “Actor” of the story. The catalogue does not consider personas but instead refers to roles. For example, a reconciliation process could be expressed from the perspective of a doctor, a pharmacist, or a pharmacy technician. While the requirements could be the same for each of these roles, there may be subtle differences that affect the requirement or differences in the associated processes that lead to additional stories being required. In this case, additional stories may be required for a pharmacy technician discussing the need to have the reconciliation validated. While some roles existing in multiple care settings (for example a pharmacist may work in hospital services or community services), others are unique and obviously work within a single care setting (for example a general practitioner). For consistency and removal of any ambiguity though we typically define a care setting if possible even if the author considers it obvious.
* *As a patient, I want to…*
* *As a pharmacist (hospital services pharmacy), I want to…*
* *As a general practitioner (primary care general practice), I want to…*

On occasion, it may not be possible to clearly identify the role with the need that is being supported. This may be due to a lack of clarity or it may be such a generic activity that it would be excessive to duplicate the requirement for every possible role. In these circumstances, it is reasonable to refer to Care Setting or an abstract role such as a “Health Care Professional”.
* *As social care, I want to review my patient’s end of life care…*
* *As a health care professional, I want to view a trend of results over time…*
* *As hospital services accident and emergency, I want to see all patients currently admitted to the emergency department…*

It is expected that as understanding evolves, so will the definition of the role. It is more important to express the need however as a reminder so that discussion around the story can continue and the story can be refined.
## Secondary Actor
Along with the Actor (Primary Actor), Care Connect user stories also consider a “Secondary Actor”. This isn’t traditionally how a user story is defined but from the perspective of interoperability it is useful to consider who the secondary actor is to clarify the source or destination of the associated method. When presenting the user story, the secondary actor will often be omitted. If the secondary actor cannot be identified, it may suggest that the story is not actually an interoperability story at all.

For example, consider the following user story
* *As a health care professional, I want a consolidated view of the patient’s current medications.*

Given that a single data source is not clear, it suggests further refinement to fully implement. So, this story may be better expressed as several more granular stories:
* *As a health care professional (hospital services) I wish to view current medication from primary care general practice…*
* *As a health care professional (hospital services) I wish to view current medication from mental health services…*
* *As a health care professional (hospital services) I wish to view current medication from community dental services…*

This begins to better specify the need for multiple interfaces at some point which may (or may not) be serviced by their own Care Connect API. Finally, the original story remains valid as a story in this context because it provides additional detail that influences how each of the interfaces are built. Here the need for a consolidated view means that the interfaces will need to be developed to send and receive structured data. This technical requirement is being expressed in a way that would be more easily understood by a non-technical audience. This technical detail, once understood would be written into the acceptance criteria of each of the user stories to facilitate the development of the consolidated user interface.
## Requirement
The requirement forms the crux of the user story. This is the requirement expressed from the perspective of a user’s need or user’s goal. While the granularity of a story can vary, a good example should be something that doesn’t have strong dependencies on other stories and something that can be measured and tested.

Given the technical nature of interoperability, it is often tempting to think of stories in terms of the developer or the API. Ultimately, it must be remembered that the interface exists to provide clinical benefit and it shouldn’t a vehicle to demonstrate the technical proficiency of the developer or an organisation.
Consider the example:

* *As a developer, I want to receive result messages in a structured format*

A better way of phrasing this would be:

* *As a health care professional, I want to view results in a single consolidated view*

Which defers the solution to a design and development stage while presenting the requirement based on a clinical need.
## Justification
Given that a specific requirement, there should also be a reason the user wishes to do that. It is possible that the same requirement can be expressed by different users for different reasons. This ultimately influences the acceptance criteria that would then be associated to the story.

It’s possible to see in the following story examples that two requirements have different justifications. In these examples, the implication of the justification is very significant in how a solution may be delivered, how the story is triggered and what the implication of the story is to the GP receiving the discharge.
* *I want to discharge and refer a patient back to their GP because the patient cannot be contacted following a referral.*
* *I want to discharge and refer a patient back to their GP because the patient has stated that they do not want and more appointments on their cancer care pathway.*

## Acceptance Criteria
The acceptance criteria associated to each of the user stories help to bridge the gap between the clinical requirement and the technical solution. Upon the initial creation of the story, it is expected that acceptance criteria are limited to outcomes that are visible to the clinicians (actors) associated to the story. As conversation continues between development and the client, the criteria can include more technical expectations that wouldn’t necessarily be understood by the clinical audience.
## Organising User Stories
To help organise user stories, features may be used to group related stories in a way that presents all the user needs that need to be expressed to fully support an area of functionality. The use of Epics and Themes is avoided because this aligns very closely to the agile development process called Scrum which is not the intention of this catalogue to align with a development methodology.
