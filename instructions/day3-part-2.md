## FHIR Bundles
Once again you might want to allocate more time to the initial setup of the project here and have a smaller time allocation to testing end to end.

There are various approaches you can take here.
1. Create a postman bundle that you share with everyone somehow.
2. Give everyone access to the ethiopia-on-platform repo and have them run the k6 script to send data
3. Have them write their own FHIR bundles
4. Login to OpenHIM on QA and pull some requests from there (although would need to add the orgs first).

### Create organizations
```json
{
    "resourceType": "Bundle",
    "type": "transaction",
    "entry": [
        {
            "resource": {
                "resourceType": "Organization",
                "id": "009a6a861c1b45778c0cbedadefe52a4",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "141010063"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "xQcwHlb5f7a"
                    }
                ],
                "active": true,
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "code": "prov",
                                "display": "Healthcare Provider"
                            }
                        ]
                    }
                ],
                "name": "Teklehaymanot medium clinic",
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000003",
                        "use": "work"
                    }
                ],
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "Organization/009a6a861c1b45778c0cbedadefe52a4"
            }
        },
        {
            "resource": {
                "resourceType": "Organization",
                "id": "878066e1-cca1-406e-ab74-fe49040aeec0",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "111"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "DGjspVpNRWY"
                    }
                ],
                "active": true,
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "code": "prov",
                                "display": "Healthcare Provider"
                            }
                        ]
                    }
                ],
                "name": "22 Maazoria Higher Clinic",
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000003",
                        "use": "work"
                    }
                ],
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Bole Sub City",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "Organization/878066e1-cca1-406e-ab74-fe49040aeec0"
            }
        },
        {
            "resource": {
                "resourceType": "Organization",
                "id": "90e0848e-0674-4f3d-af15-8b2f43530453",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "222"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "zHir1atyWSU"
                    }
                ],
                "active": true,
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "code": "prov",
                                "display": "Healthcare Provider"
                            }
                        ]
                    }
                ],
                "name": "3S Pedatric Specality Clinc",
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000003",
                        "use": "work"
                    }
                ],
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Lideta Sub City",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "Organization/90e0848e-0674-4f3d-af15-8b2f43530453"
            }
        },
        {
            "resource": {
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2021-09-27T12:36:43.000+00:00",
                    "source": "#qlEFrVn4Kr0jUJJT"
                },
                "active": true,
                "id": "18d5a42102424a9586867549b5abb350",
                "resourceType": "Organization",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "141050012"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "display": "Healthcare Provider",
                                "code": "prov"
                            }
                        ]
                    }
                ],
                "address": [
                    {
                        "city": "Horo Gudru Welega",
                        "state": "Oromia",
                        "line": [
                            "Ref Balcha Hamile"
                        ],
                        "district": "Hababo Gudru"
                    }
                ],
                "name": "Dj Balcha Hospital"
            },
            "request": {
                "method": "PUT",
                "url": "Organization/18d5a42102424a9586867549b5abb350"
            }
        },
        {
            "resource": {
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2021-09-27T12:41:09.000+00:00",
                    "source": "#40prM4CLrTYzFp8d"
                },
                "active": true,
                "id": "b6e9f3f4307c4d12914a4ceba24f9217",
                "resourceType": "Organization",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "306120023"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "KZfdQbGXABc"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "display": "Healthcare Provider",
                                "code": "prov"
                            }
                        ]
                    }
                ],
                "address": [
                    {
                        "city": "East Gojam",
                        "state": "Amhara",
                        "line": [
                            "Ref Balcha Hamile"
                        ],
                        "district": "Awabel"
                    }
                ],
                "name": "Wojel Health Center"
            },
            "request": {
                "method": "PUT",
                "url": "Organization/b6e9f3f4307c4d12914a4ceba24f9217"
            }
        },
        {
            "resource": {
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2021-09-27T12:49:09.000+00:00",
                    "source": "#SM7EDfMuLn9ehHd0"
                },
                "active": true,
                "id": "7c18655bec4542fd8d323045b8d953d4",
                "resourceType": "Organization",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "419040024"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "JsM59TuriZg"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "display": "Healthcare Provider",
                                "code": "prov"
                            }
                        ]
                    }
                ],
                "address": [
                    {
                        "city": "Horo Gudru Welega",
                        "state": "Oromia",
                        "line": [
                            "Ref Toko Tane Hamile"
                        ],
                        "district": "Hababo Gudru"
                    }
                ],
                "name": "Kenate Biya Health Center"
            },
            "request": {
                "method": "PUT",
                "url": "Organization/7c18655bec4542fd8d323045b8d953d4"
            }
        },
        {
            "resource": {
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2021-09-27T12:55:13.000+00:00",
                    "source": "#A2NbGgtGWC0lO6j8"
                },
                "active": true,
                "id": "1490b3ca120c457b998b8d5b719d8378",
                "resourceType": "Organization",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MOHId",
                        "value": "204050011"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/HFUID",
                        "value": "MxsObjvc3WV"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                                "display": "Healthcare Provider",
                                "code": "prov"
                            }
                        ]
                    }
                ],
                "address": [
                    {
                        "city": "Fanti  (zone 4)",
                        "state": "Afar",
                        "line": [
                            "Kebele 01"
                        ],
                        "district": "Golina"
                    }
                ],
                "name": "Kelewan District Hospital"
            },
            "request": {
                "method": "PUT",
                "url": "Organization/1490b3ca120c457b998b8d5b719d8378"
            }
        }
    ]
}
```

### Create 3 patients with some patient data
```json
{
    "resourceType": "Bundle",
    "type": "transaction",
    "entry": [
        {
            "resource": {
                "resourceType": "RelatedPerson",
                "id": "f19e4475-ebbc-497e-8116-bf0ead7334d0",
                "patient": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "relationship": [
                    {
                        "text": "child"
                    },
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v3-RoleCode",
                                "code": "FAMMEMB"
                            }
                        ]
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Doe"
                        ]
                    }
                ],
                "gender": "male",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "f19e4475-ebbc-497e-8116-bf0ead7334d0"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "001c260e-159e-4a6e-8c9c-3a8c5fc61ba2"
                    }
                ],
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/fbict-registration-date",
                        "valueDateTime": "1989-08-14"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "RelatedPerson/f19e4475-ebbc-497e-8116-bf0ead7334d0"
            }
        },
        {
            "resource": {
                "resourceType": "Patient",
                "id": "6ff29b6a-3563-43c7-b2e2-a5330df259c6",
                "extension": [
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-religion",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/ValueSet/v3-ReligiousAffiliation",
                                    "code": "1036",
                                    "display": "Orthodox"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-relatedPerson",
                        "valueReference": {
                            "reference": "RelatedPerson/f19e4475-ebbc-497e-8116-bf0ead7334d0"
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/EducationalLevel",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/CodeSystem/v3-EducationLevel",
                                    "code": "ELEM",
                                    "display": "Elementary School"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/Occupation",
                        "valueString": "Foreman"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/SmartCareID",
                        "value": "6ff29b6a-3563-43c7-b2e2-a5330df259c6"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "MRN-6ff29b6a-3563-43c7-b2e2-a5330df259c6"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "UAN-6ff29b6a-3563-43c7-b2e2-a5330df259c6"
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Jhon"
                        ]
                    }
                ],
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000000",
                        "use": "home"
                    }
                ],
                "gender": "female",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "maritalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-MaritalStatus",
                            "code": "M",
                            "display": "Married"
                        }
                    ]
                },
                "managingOrganization": {
                    "reference": "Organization/009a6a861c1b45778c0cbedadefe52a4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "de49609d-683b-46fc-a1b3-0254c16b5876",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/care-plan",
                                "code": "hiv-positive-tracking",
                                "display": "HIV Positive Tracking"
                            }
                        ]
                    }
                ],
                "status": "active",
                "intent": "order",
                "created": "1997-09-22",
                "period": {
                    "start": "2003-07-11",
                    "end": "2020-09-13"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "supportingInfo": {
                    "reference": "ServiceRequest/fbe565f9-94a9-422e-a902-1c77548eaee2"
                },
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "started-art",
                                        "display": "Started ART"
                                    }
                                ]
                            },
                            "status": "in-progress",
                            "statusReason": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking/status-reason",
                                        "code": ""
                                    }
                                ]
                            },
                            "description": "Address adherence barriers"
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "linked-to-care",
                                        "display": "Linked to care and treatment"
                                    }
                                ]
                            },
                            "status": "not-started",
                            "scheduledPeriod": {
                                "start": "2006-07-16"
                            }
                        }
                    },
                    {
                        "extension": [
                            {
                                "url": "http://cdr.aacahb.gov.et/FinalOutcomeKnown",
                                "valueBoolean": true
                            }
                        ],
                        "outcomeCodeableConcept": [
                            {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/final-outcome",
                                        "code": "started-art-in-other-hf",
                                        "display": "Started ART in other HF"
                                    }
                                ]
                            }
                        ],
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "final-outcome",
                                        "display": "Final Outcome"
                                    }
                                ]
                            },
                            "kind": "ServiceRequest",
                            "location": {
                                "display": "Teklehaymanot medium clinic"
                            },
                            "scheduledPeriod": {
                                "start": "2000-05-05"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/de49609d-683b-46fc-a1b3-0254c16b5876"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "22d4bd00-6965-4a1f-b6ce-e75b94b2cb21",
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "text": "Cryotherapy",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/precancerous-treatment",
                                        "code": "cryotherapy",
                                        "display": "Cryotherapy"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "precancerous lesion",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "285636001",
                                            "display": "Cervical intraepithelial neoplasia"
                                        }
                                    ]
                                }
                            ]
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "text": "Treated at the facility",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/suspicious-cancerous-treatment",
                                        "code": "treated-at-facility",
                                        "display": "Treated at the facility"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "Suspected cervical cancer",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "315266007",
                                            "display": "Suspected cervical cancer"
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ],
                "status": "completed",
                "category": [
                    {
                        "text": "Cervical cancer care plan",
                        "coding": [
                            {
                                "code": "cervical-cancer-care-plan",
                                "system": "http://cdr.aacahb.gov.et/cervical-cancer-care-plan",
                                "display": "Cervical cancer care plan"
                            }
                        ]
                    }
                ],
                "extension": [
                    {
                        "valueDateTime": "2025-05-16",
                        "url": "http://cdr.aacahb.gov.et/next-appintment-date"
                    }
                ],
                "intent": "order",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/22d4bd00-6965-4a1f-b6ce-e75b94b2cb21"
            }
        },
        {
            "resource": {
                "resourceType": "DiagnosticReport",
                "id": "a4fa055f-d462-4818-9258-5c8e61b76224",
                "status": "final",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                                "code": "LAB",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "viral load"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "effectivePeriod": {
                    "start": "1999-10-11",
                    "end": "1998-02-23"
                },
                "conclusion": "Suppressed"
            },
            "request": {
                "method": "PUT",
                "url": "DiagnosticReport/a4fa055f-d462-4818-9258-5c8e61b76224"
            }
        },
        {
            "resource": {
                "resourceType": "Encounter",
                "id": "b28d5a38-e6da-42ae-b2be-a7bffaae84c4",
                "status": "finished",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/visit-type",
                        "valueString": "Scheduled"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/next-visit",
                        "valueDateTime": "2015-05-25"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Encounter",
                        "value": "900326"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "390906007"
                            }
                        ],
                        "text": "Follow-up encounter"
                    }
                ],
                "serviceType": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/service-type",
                            "code": "536",
                            "display": "Art therapy"
                        },
                        {
                            "system": "http://snomed.info/sct",
                            "code": "65153003",
                            "display": "Art therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "period": {
                    "start": "2019-09-18",
                    "end": "2003-08-11"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationDispense",
                "id": "bf45e1ab-de6c-489c-9604-6ac28c5ca9c3",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/was-switched",
                        "valueBoolean": false
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-type",
                        "valueString": "3rd switch"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-reason",
                        "valueString": "Clinical failure"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/dose-end-date",
                        "valueDateTime": "2001-02-06"
                    }
                ],
                "status": "completed",
                "statusReasonCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/medication-dispense/status-reason",
                            "code": "restart"
                        }
                    ]
                },
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/hiv-regimen-codes",
                            "code": "1g"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "quantity": {
                    "value": 146,
                    "system": "http://terminology.hl7.org/CodeSystem/v3-orderableDrugForm",
                    "code": "Tablet",
                    "unit": "Tablet"
                },
                "daysSupply": {
                    "value": 39,
                    "unit": "Day",
                    "system": "http://unitsofmeasure.org",
                    "code": "d"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationDispense/bf45e1ab-de6c-489c-9604-6ac28c5ca9c3"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "5ae47bb2-1a96-4a65-ad6c-71510c46d49f",
                "status": "active",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "effectivePeriod": {
                    "start": "2019-09-22"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/arv-therapy",
                                "code": "arv-treatment",
                                "display": "ARV Treatment started"
                            }
                        ],
                        "text": "ARV Treatment started"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/5ae47bb2-1a96-4a65-ad6c-71510c46d49f"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "0e5b07a0-112b-4bd7-b97c-63dd9dda4570",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "INH1"
                    }
                ],
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "status": "completed",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "699618001",
                            "display": "Tuberculosis preventive therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "effectivePeriod": {
                    "start": "1993-01-24",
                    "end": "2011-12-26"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/prophylaxis-type",
                                "code": "alternate"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/0e5b07a0-112b-4bd7-b97c-63dd9dda4570"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "dcb5c671-d44e-41fc-8b87-a7ef827ff86b",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "TBRx1"
                    }
                ],
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "status": "active",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "tb-treatment",
                            "display": "TB Treatment"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "effectivePeriod": {
                    "start": "1994-11-30",
                    "end": "1996-07-24"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "56717001",
                                "display": "Tuberculosis (disorder)"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/dcb5c671-d44e-41fc-8b87-a7ef827ff86b"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "42cfec0c-c162-40e3-a3c2-90dbd704d91f",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/Adherence-level",
                        "valueString": "good"
                    }
                ],
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "398731002",
                            "display": "Product containing sulfamethoxazole and trimethoprim"
                        }
                    ],
                    "text": "Co-trimoxazole"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "effectivePeriod": {
                    "start": "2007-01-30",
                    "end": "2021-05-12"
                },
                "dosage": [
                    {
                        "maxDosePerPeriod": {
                            "numerator": {
                                "value": 30,
                                "unit": "Dose",
                                "system": "http://unitsofmeasure.org",
                                "code": "Dose"
                            },
                            "denominator": {
                                "value": 30,
                                "unit": "days",
                                "system": "http://unitsofmeasure.org",
                                "code": "d"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/42cfec0c-c162-40e3-a3c2-90dbd704d91f"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "382c8154-5876-490f-aacd-bce72a5a620c",
                "context": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "387174006",
                            "display": "Fluconazole"
                        }
                    ],
                    "text": "Fluconazole"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "effectivePeriod": {
                    "start": "1988-04-23",
                    "end": "2007-10-07"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/382c8154-5876-490f-aacd-bce72a5a620c"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "03fe697b-a522-40be-adf7-62b75c6ca954",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "partOf": [
                    {
                        "reference": "MedicationDispense/bf45e1ab-de6c-489c-9604-6ac28c5ca9c3"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "418633004",
                            "display": "Medication adherence"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "135815002",
                            "display": "Good"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/03fe697b-a522-40be-adf7-62b75c6ca954"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "b361bcd7-0281-4b1c-940c-eeb6688725c2",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "social-history",
                                "display": "Social History"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "87276001",
                            "display": "Nutritional status"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "717928006",
                            "display": "MAM"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/b361bcd7-0281-4b1c-940c-eeb6688725c2"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "2e858f04-3bab-4e3e-9001-25c793be75e1",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "vital-signs",
                                "display": "Vital Signs"
                            }
                        ],
                        "text": "Vital Signs"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://loinc.org",
                            "code": "29463-7",
                            "display": "Body weight"
                        }
                    ],
                    "text": "Weight"
                },
                "valueQuantity": {
                    "value": 70,
                    "unit": "kilogram",
                    "system": "http://unitsofmeasure.org",
                    "code": "kg"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/2e858f04-3bab-4e3e-9001-25c793be75e1"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "346e7e01-1e5d-48f5-b2be-f112724d9937",
                "status": "final",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Laoratory",
                        "value": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                    }
                ],
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "laboratory",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "Viral load count"
                },
                "valueQuantity": {
                    "value": 1990,
                    "unit": "Count",
                    "system": "http://unitsofmeasure.org",
                    "code": "{Count}"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/346e7e01-1e5d-48f5-b2be-f112724d9937"
            }
        },
        {
            "resource": {
                "id": "5180f389-0aec-44b2-9f3c-bf27f1e24d1c",
                "resourceType": "Procedure",
                "status": "not-done",
                "category": {
                    "text": "Screening",
                    "coding": [
                        {
                            "code": "20135006",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "Cervical cancer screening",
                    "coding": [
                        {
                            "code": "243877001",
                            "system": "http://snomed.info/sct",
                            "display": "Cancer cervix screening status"
                        }
                    ]
                },
                "performedDateTime": "1999-06-03",
                "extension": [
                    {
                        "valueBoolean": false,
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/5180f389-0aec-44b2-9f3c-bf27f1e24d1c"
            }
        },
        {
            "resource": {
                "id": "fa44585d-d4b0-4c9c-88ca-1e6a208635b7",
                "resourceType": "Procedure",
                "status": "completed",
                "category": {
                    "text": "Laboratory procedure",
                    "coding": [
                        {
                            "code": "108252007",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "viral load",
                    "coding": [
                        {
                            "code": "315124004",
                            "system": "http://snomed.info/sct",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ]
                },
                "report": [
                    {
                        "reference": "DiagnosticReport/cc71ecc72acf4f7f9a1b14dc3bc10767"
                    }
                ],
                "extension": [
                    {
                        "valueString": "Routine",
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "reasonCode": [
                    {
                        "text": "Annual VL Test"
                    }
                ],
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/fa44585d-d4b0-4c9c-88ca-1e6a208635b7"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "c439856a-f415-4e45-b81f-d7a8e0f59b58",
                "questionnaire": "PregnancyStatus",
                "status": "completed",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "item": [
                    {
                        "linkId": "pregnant",
                        "text": "Is Pregnant",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "pregnant.want-to-be-pregnant",
                                        "text": "Want to be pregnant",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "is-breast-feeding",
                        "text": "Is breast feeding",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/c439856a-f415-4e45-b81f-d7a8e0f59b58"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "0d968ceb-27cb-469d-ac36-1ecd6687d74a",
                "questionnaire": "ARTEligibility",
                "status": "completed",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "source": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "item": [
                    {
                        "linkId": "hiv-confirmation-date",
                        "text": "HIV Confirmed Date",
                        "answer": [
                            {
                                "valueDate": "2005-09-15"
                            }
                        ]
                    },
                    {
                        "linkId": "eligbility",
                        "item": [
                            {
                                "linkId": "eligbility.eligbile",
                                "text": "Eligible for ART",
                                "answer": [
                                    {
                                        "valueBoolean": true,
                                        "item": [
                                            {
                                                "linkId": "eligbility.eligbile.why",
                                                "text": "Why Eligible",
                                                "answer": [
                                                    {
                                                        "valueString": "Transfer In"
                                                    }
                                                ]
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/0d968ceb-27cb-469d-ac36-1ecd6687d74a"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "d21a8d5f-015a-45e0-a521-598bb3b7549d",
                "questionnaire": "AppointmentSpacingModel",
                "status": "completed",
                "encounter": {
                    "reference": "Encounter/b28d5a38-e6da-42ae-b2be-a7bffaae84c4"
                },
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "item": [
                    {
                        "linkId": "assessment",
                        "item": [
                            {
                                "linkId": "assessment.assessed",
                                "text": "Assessed For ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "assessment.date",
                                "text": "Assessed Date",
                                "answer": [
                                    {
                                        "valueDate": [
                                            "1994-04-05"
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "category",
                        "text": "Category",
                        "answer": [
                            {
                                "valueString": "Category 1a"
                            }
                        ]
                    },
                    {
                        "linkId": "eligible",
                        "text": "Is Eligible For ASM",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "counseled",
                        "text": "Counseled",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "enrollment",
                        "item": [
                            {
                                "linkId": "enrollment.agree",
                                "text": "Agree To Be Enrolled",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.enrolled",
                                "text": "Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": true
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.reason",
                                "text": "Reason Not Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.date",
                                "text": "Enrollment Date",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "couple-enrollment",
                        "item": [
                            {
                                "linkId": "couple-enrollment.enrolled",
                                "text": "Couple Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": true
                                    }
                                ]
                            },
                            {
                                "linkId": "couple-enrollment.uat-no",
                                "text": "Couple UAT No",
                                "answer": [
                                    {
                                        "valueString": "6b18d435-f2d0-4db4-bc31-fb848c32038c"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "new-category-change",
                        "item": [
                            {
                                "linkId": "new-category-change.type",
                                "text": "New Category Change",
                                "answer": [
                                    {
                                        "valueBoolean": [
                                            false
                                        ]
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.reason",
                                "text": "Reason For Category Change",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.date",
                                "text": "Category Change Date",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "termination",
                        "item": [
                            {
                                "linkId": "termination.terminated",
                                "text": "Terminated From ASM",
                                "answer": [
                                    {
                                        "valueBoolean": true
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.reason",
                                "text": "Reason For Termination",
                                "answer": [
                                    {
                                        "valueString": "Other"
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.date",
                                "text": "Terminated Date",
                                "answer": [
                                    {
                                        "valueDate": "2019-07-22"
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/d21a8d5f-015a-45e0-a521-598bb3b7549d"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "436804a1-25dd-4798-94b9-41305d99f562",
                "questionnaire": "IndexCaseContactScreening",
                "status": "completed",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "item": [
                    {
                        "linkId": "screening-date",
                        "text": "Follow Up Date",
                        "answer": [
                            {
                                "valueDate": "2017-08-23"
                            }
                        ]
                    },
                    {
                        "linkId": "client-eligible",
                        "text": "Is the client eligible for Partner and Family Based ICT?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "newly-enrolled",
                        "text": "Is the client newly enrolled (Diagnosed)",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "high-viral-load",
                        "text": "Is the client with high viral load (HVL) (2>1000c/ml)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "restart",
                        "text": "Is the client drop and return (Restart)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "new-partner",
                        "text": "Is the client with new partner?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "sti-care",
                        "text": "Has the client in care with STI?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-disclosed",
                        "text": "Is the client with partner not yet disclosed?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-tested",
                        "text": "Is the client with partner not tested?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "client-child-not-tested",
                        "text": "Is the client child (<15 years) not tested?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "kp-client",
                        "text": "Is the kp (FSW)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "maternal-hiv-status",
                        "text": "Maternal HIV status?",
                        "answer": [
                            {
                                "valueString": "Unknown status & alive"
                            }
                        ]
                    },
                    {
                        "linkId": "marital-status",
                        "text": "Marital status?",
                        "answer": [
                            {
                                "valueString": "Single"
                            }
                        ]
                    },
                    {
                        "linkId": "fbict-service",
                        "text": "Is the client (index case) offered with partner FBICT service?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "offer-accepted",
                        "text": "Has the client accepted the offer?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contacts-elicited",
                        "text": "Number of contacts elicited?",
                        "answer": [
                            {
                                "valueString": 3
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/436804a1-25dd-4798-94b9-41305d99f562"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "c4b444b3-2512-42a3-8dd8-358b22c7d012",
                "questionnaire": "IndexCaseFamilyContact",
                "status": "completed",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                },
                "source": {
                    "reference": "RelatedPerson/f19e4475-ebbc-497e-8116-bf0ead7334d0"
                },
                "item": [
                    {
                        "linkId": "contact-prev-tested",
                        "text": "Contact previously been tested",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "contact-prev-tested.date",
                                        "text": "Previous date tested",
                                        "answer": [
                                            {
                                                "valueDate": "1996-03-28"
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-prev-tested.result",
                                        "text": "Previous HIV test result",
                                        "answer": [
                                            {
                                                "valueString": "Negative"
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "contact-counseled",
                        "text": "Is the contact counseled for HIV today",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "hiv-care-linked",
                        "text": "Linked to HIV care",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contact-tested",
                        "text": "Has the contact tested for HIV",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "contact-tested.date",
                                        "text": "Date tested",
                                        "answer": [
                                            {
                                                "valueDate": "2019-10-21"
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-tested.result",
                                        "text": "HIV test result",
                                        "answer": [
                                            {
                                                "valueString": "Negative"
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "not-testing-reason",
                        "text": "Reason for not testing",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "partner-started-art",
                        "text": "Has the partner started ART",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "client-health-status",
                        "text": "Health status of the client",
                        "answer": [
                            {
                                "valueString": "Healthy"
                            }
                        ]
                    },
                    {
                        "linkId": "living-with-index",
                        "text": "Currently living with index case",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contact-mrn",
                        "text": "Contact MRN",
                        "answer": [
                            {
                                "valueString": "4c1de1f6-e2d5-4849-9277-d3436d0f7f24"
                            }
                        ]
                    },
                    {
                        "linkId": "contact-uan",
                        "text": "Contact UAN",
                        "answer": [
                            {
                                "valueString": "84d9af19-5012-4a9f-9151-2cbd87093cad"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/c4b444b3-2512-42a3-8dd8-358b22c7d012"
            }
        },
        {
            "resource": {
                "resourceType": "ServiceRequest",
                "id": "fbe565f9-94a9-422e-a902-1c77548eaee2",
                "basedOn": [
                    {
                        "reference": "CarePlan/de49609d-683b-46fc-a1b3-0254c16b5876"
                    }
                ],
                "status": "active",
                "code": {
                    "text": "From Within Facility",
                    "coding": [
                        {
                            "display": "Internal facility referral or transfer",
                            "system": "http://loinc.org",
                            "code": "LA9328-1"
                        }
                    ]
                },
                "locationCode": [
                    {
                        "text": "My City"
                    }
                ],
                "intent": "plan",
                "subject": {
                    "reference": "Patient/66a07ff6-58a6-4de4-ae27-0378f8a71cc8"
                }
            },
            "request": {
                "method": "PUT",
                "url": "ServiceRequest/fbe565f9-94a9-422e-a902-1c77548eaee2"
            }
        },
        {
            "resource": {
                "resourceType": "RelatedPerson",
                "id": "240dfe61-bf7d-4dca-be3f-7b6badd36ddc",
                "patient": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "relationship": [
                    {
                        "text": "sexual-partner"
                    },
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v3-RoleCode",
                                "code": "FAMMEMB"
                            }
                        ]
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Doe"
                        ]
                    }
                ],
                "gender": "male",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "240dfe61-bf7d-4dca-be3f-7b6badd36ddc"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "64fe8058-3813-48bd-838e-f68caade75e5"
                    }
                ],
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/fbict-registration-date",
                        "valueDateTime": "2006-02-03"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "RelatedPerson/240dfe61-bf7d-4dca-be3f-7b6badd36ddc"
            }
        },
        {
            "resource": {
                "resourceType": "Patient",
                "id": "f865c03b-2b85-4b1f-8d0f-9e7ef2039273",
                "extension": [
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-religion",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/ValueSet/v3-ReligiousAffiliation",
                                    "code": "1036",
                                    "display": "Orthodox"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-relatedPerson",
                        "valueReference": {
                            "reference": "RelatedPerson/240dfe61-bf7d-4dca-be3f-7b6badd36ddc"
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/EducationalLevel",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/CodeSystem/v3-EducationLevel",
                                    "code": "ELEM",
                                    "display": "Elementary School"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/Occupation",
                        "valueString": "Foreman"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/SmartCareID",
                        "value": "f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "MRN-f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "UAN-f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Jhon"
                        ]
                    }
                ],
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000000",
                        "use": "home"
                    }
                ],
                "gender": "female",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "maritalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-MaritalStatus",
                            "code": "M",
                            "display": "Married"
                        }
                    ]
                },
                "managingOrganization": {
                    "reference": "Organization/009a6a861c1b45778c0cbedadefe52a4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "323218c5-c445-40f9-abf3-72e1cf5d7f3e",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/care-plan",
                                "code": "hiv-positive-tracking",
                                "display": "HIV Positive Tracking"
                            }
                        ]
                    }
                ],
                "status": "active",
                "intent": "order",
                "created": "2008-03-29",
                "period": {
                    "start": "2006-07-10",
                    "end": "2020-09-13"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "supportingInfo": {
                    "reference": "ServiceRequest/7c566a82-c278-4df0-a49f-d1301fc10ac2"
                },
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "started-art",
                                        "display": "Started ART"
                                    }
                                ]
                            },
                            "status": "in-progress",
                            "statusReason": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking/status-reason",
                                        "code": ""
                                    }
                                ]
                            },
                            "description": "Address adherence barriers"
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "linked-to-care",
                                        "display": "Linked to care and treatment"
                                    }
                                ]
                            },
                            "status": "completed",
                            "scheduledPeriod": {
                                "start": "1997-01-25"
                            }
                        }
                    },
                    {
                        "extension": [
                            {
                                "url": "http://cdr.aacahb.gov.et/FinalOutcomeKnown",
                                "valueBoolean": true
                            }
                        ],
                        "outcomeCodeableConcept": [
                            {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/final-outcome",
                                        "code": "died",
                                        "display": "Died"
                                    }
                                ]
                            }
                        ],
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "final-outcome",
                                        "display": "Final Outcome"
                                    }
                                ]
                            },
                            "kind": "ServiceRequest",
                            "location": {
                                "display": ""
                            },
                            "scheduledPeriod": {
                                "start": "1998-01-24"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/323218c5-c445-40f9-abf3-72e1cf5d7f3e"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "79a48d08-e1fb-4143-b5c4-b8d4a2da158e",
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "text": "Cryotherapy",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/precancerous-treatment",
                                        "code": "cryotherapy",
                                        "display": "Cryotherapy"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "precancerous lesion",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "285636001",
                                            "display": "Cervical intraepithelial neoplasia"
                                        }
                                    ]
                                }
                            ]
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "text": "Treated at the facility",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/suspicious-cancerous-treatment",
                                        "code": "treated-at-facility",
                                        "display": "Treated at the facility"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "Suspected cervical cancer",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "315266007",
                                            "display": "Suspected cervical cancer"
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ],
                "status": "completed",
                "category": [
                    {
                        "text": "Cervical cancer care plan",
                        "coding": [
                            {
                                "code": "cervical-cancer-care-plan",
                                "system": "http://cdr.aacahb.gov.et/cervical-cancer-care-plan",
                                "display": "Cervical cancer care plan"
                            }
                        ]
                    }
                ],
                "extension": [
                    {
                        "valueDateTime": "2025-05-16",
                        "url": "http://cdr.aacahb.gov.et/next-appintment-date"
                    }
                ],
                "intent": "order",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                }
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/79a48d08-e1fb-4143-b5c4-b8d4a2da158e"
            }
        },
        {
            "resource": {
                "resourceType": "DiagnosticReport",
                "id": "810baf38-61ff-40f2-983b-30ecda06c456",
                "status": "final",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                                "code": "LAB",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "viral load"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "effectivePeriod": {
                    "start": "1990-03-10",
                    "end": "2019-01-12"
                },
                "conclusion": "Unsuppressed"
            },
            "request": {
                "method": "PUT",
                "url": "DiagnosticReport/810baf38-61ff-40f2-983b-30ecda06c456"
            }
        },
        {
            "resource": {
                "resourceType": "Encounter",
                "id": "982c8ffa-2e8a-40d2-8d80-ee2286180472",
                "status": "finished",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/visit-type",
                        "valueString": "Unscheduled"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/next-visit",
                        "valueDateTime": "1992-09-13"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Encounter",
                        "value": "900326"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "390906007"
                            }
                        ],
                        "text": "Follow-up encounter"
                    }
                ],
                "serviceType": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/service-type",
                            "code": "536",
                            "display": "Art therapy"
                        },
                        {
                            "system": "http://snomed.info/sct",
                            "code": "65153003",
                            "display": "Art therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "period": {
                    "start": "2004-01-14",
                    "end": "2002-05-30"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationDispense",
                "id": "a603b5a8-b77c-4b68-b3e3-3f7b5fc5e404",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/was-switched",
                        "valueBoolean": true
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-type",
                        "valueString": "1st switch"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-reason",
                        "valueString": "Clinical failure"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/dose-end-date",
                        "valueDateTime": "1992-03-02"
                    }
                ],
                "status": "completed",
                "statusReasonCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/medication-dispense/status-reason",
                            "code": "to"
                        }
                    ]
                },
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/hiv-regimen-codes",
                            "code": "4L"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "quantity": {
                    "value": 95,
                    "system": "http://terminology.hl7.org/CodeSystem/v3-orderableDrugForm",
                    "code": "Tablet",
                    "unit": "Tablet"
                },
                "daysSupply": {
                    "value": 150,
                    "unit": "Day",
                    "system": "http://unitsofmeasure.org",
                    "code": "d"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationDispense/a603b5a8-b77c-4b68-b3e3-3f7b5fc5e404"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "cdae55c4-9176-43d0-8eee-9e8f3474665b",
                "status": "not-taken",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "effectivePeriod": {
                    "start": "1993-05-28"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/arv-therapy",
                                "code": "arv-treatment",
                                "display": "ARV Treatment started"
                            }
                        ],
                        "text": "ARV Treatment started"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/cdae55c4-9176-43d0-8eee-9e8f3474665b"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "6fd59c7b-b8b9-49a3-a343-be572c25585c",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "INH1"
                    }
                ],
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "status": "stopped",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "699618001",
                            "display": "Tuberculosis preventive therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "effectivePeriod": {
                    "start": "2003-10-20",
                    "end": "1989-09-07"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/prophylaxis-type",
                                "code": "inh"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/6fd59c7b-b8b9-49a3-a343-be572c25585c"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "74028275-672e-46d0-88e1-3c728d1e4239",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "TBRx1"
                    }
                ],
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "status": "stopped",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "tb-treatment",
                            "display": "TB Treatment"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "effectivePeriod": {
                    "start": "2001-10-18",
                    "end": "1987-02-09"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "56717001",
                                "display": "Tuberculosis (disorder)"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/74028275-672e-46d0-88e1-3c728d1e4239"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "b06629d5-f6ba-4884-91b7-b8d637574542",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/Adherence-level",
                        "valueString": "good"
                    }
                ],
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "398731002",
                            "display": "Product containing sulfamethoxazole and trimethoprim"
                        }
                    ],
                    "text": "Co-trimoxazole"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "effectivePeriod": {
                    "start": "1997-09-01",
                    "end": "2004-02-10"
                },
                "dosage": [
                    {
                        "maxDosePerPeriod": {
                            "numerator": {
                                "value": 30,
                                "unit": "Dose",
                                "system": "http://unitsofmeasure.org",
                                "code": "Dose"
                            },
                            "denominator": {
                                "value": 30,
                                "unit": "days",
                                "system": "http://unitsofmeasure.org",
                                "code": "d"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/b06629d5-f6ba-4884-91b7-b8d637574542"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "faa1c867-49db-4b42-83e1-312c4ed5bc1b",
                "context": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "387174006",
                            "display": "Fluconazole"
                        }
                    ],
                    "text": "Fluconazole"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "effectivePeriod": {
                    "start": "2013-01-30",
                    "end": "2001-05-19"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/faa1c867-49db-4b42-83e1-312c4ed5bc1b"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "8d2f5745-b395-42ad-a2cf-d226f9a7311d",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "partOf": [
                    {
                        "reference": "MedicationDispense/a603b5a8-b77c-4b68-b3e3-3f7b5fc5e404"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "418633004",
                            "display": "Medication adherence"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "135817005",
                            "display": "Fair"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/8d2f5745-b395-42ad-a2cf-d226f9a7311d"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "900a54d1-c9ae-40b5-8e28-24591b356111",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "social-history",
                                "display": "Social History"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "87276001",
                            "display": "Nutritional status"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "24484000",
                            "display": "Severe Malnutrition"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/900a54d1-c9ae-40b5-8e28-24591b356111"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "9d05bd89-f0fe-436b-8dc4-32989a361cb3",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "vital-signs",
                                "display": "Vital Signs"
                            }
                        ],
                        "text": "Vital Signs"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://loinc.org",
                            "code": "29463-7",
                            "display": "Body weight"
                        }
                    ],
                    "text": "Weight"
                },
                "valueQuantity": {
                    "value": 21,
                    "unit": "kilogram",
                    "system": "http://unitsofmeasure.org",
                    "code": "kg"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/9d05bd89-f0fe-436b-8dc4-32989a361cb3"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "382dde0f-566d-4a12-ab2f-b7766b7e3c99",
                "status": "final",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Laoratory",
                        "value": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                    }
                ],
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "laboratory",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "Viral load count"
                },
                "valueQuantity": {
                    "value": 967,
                    "unit": "Count",
                    "system": "http://unitsofmeasure.org",
                    "code": "{Count}"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/382dde0f-566d-4a12-ab2f-b7766b7e3c99"
            }
        },
        {
            "resource": {
                "id": "14cf84f2-b51f-4d47-87f8-959e281745d8",
                "resourceType": "Procedure",
                "status": "not-done",
                "category": {
                    "text": "Screening",
                    "coding": [
                        {
                            "code": "20135006",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "Cervical cancer screening",
                    "coding": [
                        {
                            "code": "243877001",
                            "system": "http://snomed.info/sct",
                            "display": "Cancer cervix screening status"
                        }
                    ]
                },
                "performedDateTime": "2008-03-02",
                "extension": [
                    {
                        "valueBoolean": false,
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/14cf84f2-b51f-4d47-87f8-959e281745d8"
            }
        },
        {
            "resource": {
                "id": "ad0ffecd-7e53-431d-8679-32394257e817",
                "resourceType": "Procedure",
                "status": "completed",
                "category": {
                    "text": "Laboratory procedure",
                    "coding": [
                        {
                            "code": "108252007",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "viral load",
                    "coding": [
                        {
                            "code": "315124004",
                            "system": "http://snomed.info/sct",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ]
                },
                "report": [
                    {
                        "reference": "DiagnosticReport/cc71ecc72acf4f7f9a1b14dc3bc10767"
                    }
                ],
                "extension": [
                    {
                        "valueString": "Targeted",
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "reasonCode": [
                    {
                        "text": "Annual VL Test"
                    }
                ],
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/ad0ffecd-7e53-431d-8679-32394257e817"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "168faca1-366f-41bc-9702-e8f2430189c3",
                "questionnaire": "PregnancyStatus",
                "status": "completed",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "item": [
                    {
                        "linkId": "pregnant",
                        "text": "Is Pregnant",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "pregnant.want-to-be-pregnant",
                                        "text": "Want to be pregnant",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "is-breast-feeding",
                        "text": "Is breast feeding",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/168faca1-366f-41bc-9702-e8f2430189c3"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "c21bcc54-169c-40e5-8409-a7242915a995",
                "questionnaire": "ARTEligibility",
                "status": "completed",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "source": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "item": [
                    {
                        "linkId": "hiv-confirmation-date",
                        "text": "HIV Confirmed Date",
                        "answer": [
                            {
                                "valueDate": "2015-08-25"
                            }
                        ]
                    },
                    {
                        "linkId": "eligbility",
                        "item": [
                            {
                                "linkId": "eligbility.eligbile",
                                "text": "Eligible for ART",
                                "answer": [
                                    {
                                        "valueBoolean": true,
                                        "item": [
                                            {
                                                "linkId": "eligbility.eligbile.why",
                                                "text": "Why Eligible",
                                                "answer": [
                                                    {
                                                        "valueString": "Transfer In"
                                                    }
                                                ]
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/c21bcc54-169c-40e5-8409-a7242915a995"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "32080a20-9bdc-4f78-8a0e-6c181e30e7b2",
                "questionnaire": "AppointmentSpacingModel",
                "status": "completed",
                "encounter": {
                    "reference": "Encounter/982c8ffa-2e8a-40d2-8d80-ee2286180472"
                },
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "item": [
                    {
                        "linkId": "assessment",
                        "item": [
                            {
                                "linkId": "assessment.assessed",
                                "text": "Assessed For ASM",
                                "answer": [
                                    {
                                        "valueBoolean": true
                                    }
                                ]
                            },
                            {
                                "linkId": "assessment.date",
                                "text": "Assessed Date",
                                "answer": [
                                    {
                                        "valueDate": [
                                            "1994-11-15"
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "category",
                        "text": "Category",
                        "answer": [
                            {
                                "valueString": "Category 1b"
                            }
                        ]
                    },
                    {
                        "linkId": "eligible",
                        "text": "Is Eligible For ASM",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "counseled",
                        "text": "Counseled",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "enrollment",
                        "item": [
                            {
                                "linkId": "enrollment.agree",
                                "text": "Agree To Be Enrolled",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.enrolled",
                                "text": "Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": true
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.reason",
                                "text": "Reason Not Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueString": "No treatment support at home"
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.date",
                                "text": "Enrollment Date",
                                "answer": [
                                    {
                                        "valueDate": "1987-12-01"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "couple-enrollment",
                        "item": [
                            {
                                "linkId": "couple-enrollment.enrolled",
                                "text": "Couple Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "couple-enrollment.uat-no",
                                "text": "Couple UAT No",
                                "answer": [
                                    {
                                        "valueString": "a5a3e58f-a0fd-428b-8d96-65f849e0cca0"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "new-category-change",
                        "item": [
                            {
                                "linkId": "new-category-change.type",
                                "text": "New Category Change",
                                "answer": [
                                    {
                                        "valueString": [
                                            "Category 1a"
                                        ]
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.reason",
                                "text": "Reason For Category Change",
                                "answer": [
                                    {
                                        "valueString": "Developed Advanced Disease"
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.date",
                                "text": "Category Change Date",
                                "answer": [
                                    {
                                        "valueDate": "1990-06-28"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "termination",
                        "item": [
                            {
                                "linkId": "termination.terminated",
                                "text": "Terminated From ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.reason",
                                "text": "Reason For Termination",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.date",
                                "text": "Terminated Date",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/32080a20-9bdc-4f78-8a0e-6c181e30e7b2"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "55b194b8-441f-400b-8e3d-da63a9ed5fa4",
                "questionnaire": "IndexCaseContactScreening",
                "status": "completed",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "item": [
                    {
                        "linkId": "screening-date",
                        "text": "Follow Up Date",
                        "answer": [
                            {
                                "valueDate": "2003-06-04"
                            }
                        ]
                    },
                    {
                        "linkId": "client-eligible",
                        "text": "Is the client eligible for Partner and Family Based ICT?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "newly-enrolled",
                        "text": "Is the client newly enrolled (Diagnosed)",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "high-viral-load",
                        "text": "Is the client with high viral load (HVL) (2>1000c/ml)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "restart",
                        "text": "Is the client drop and return (Restart)?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "new-partner",
                        "text": "Is the client with new partner?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "sti-care",
                        "text": "Has the client in care with STI?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-disclosed",
                        "text": "Is the client with partner not yet disclosed?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-tested",
                        "text": "Is the client with partner not tested?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "client-child-not-tested",
                        "text": "Is the client child (<15 years) not tested?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "kp-client",
                        "text": "Is the kp (FSW)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "maternal-hiv-status",
                        "text": "Maternal HIV status?",
                        "answer": [
                            {
                                "valueString": "Unknown status & alive"
                            }
                        ]
                    },
                    {
                        "linkId": "marital-status",
                        "text": "Marital status?",
                        "answer": [
                            {
                                "valueString": "Single"
                            }
                        ]
                    },
                    {
                        "linkId": "fbict-service",
                        "text": "Is the client (index case) offered with partner FBICT service?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "offer-accepted",
                        "text": "Has the client accepted the offer?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contacts-elicited",
                        "text": "Number of contacts elicited?",
                        "answer": [
                            {
                                "valueString": 9
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/55b194b8-441f-400b-8e3d-da63a9ed5fa4"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "cb34a18d-35a1-4efb-8df2-0ad7c9ba3c4a",
                "questionnaire": "IndexCaseFamilyContact",
                "status": "completed",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                },
                "source": {
                    "reference": "RelatedPerson/240dfe61-bf7d-4dca-be3f-7b6badd36ddc"
                },
                "item": [
                    {
                        "linkId": "contact-prev-tested",
                        "text": "Contact previously been tested",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "contact-prev-tested.date",
                                        "text": "Previous date tested",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-prev-tested.result",
                                        "text": "Previous HIV test result",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "contact-counseled",
                        "text": "Is the contact counseled for HIV today",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "hiv-care-linked",
                        "text": "Linked to HIV care",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "contact-tested",
                        "text": "Has the contact tested for HIV",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "contact-tested.date",
                                        "text": "Date tested",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-tested.result",
                                        "text": "HIV test result",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "not-testing-reason",
                        "text": "Reason for not testing",
                        "answer": [
                            {
                                "valueString": "Refused"
                            }
                        ]
                    },
                    {
                        "linkId": "partner-started-art",
                        "text": "Has the partner started ART",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "client-health-status",
                        "text": "Health status of the client",
                        "answer": [
                            {
                                "valueString": "Healthy"
                            }
                        ]
                    },
                    {
                        "linkId": "living-with-index",
                        "text": "Currently living with index case",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contact-mrn",
                        "text": "Contact MRN",
                        "answer": [
                            {
                                "valueString": "f094cd33-f22e-4f41-bcba-364a40b41d4d"
                            }
                        ]
                    },
                    {
                        "linkId": "contact-uan",
                        "text": "Contact UAN",
                        "answer": [
                            {
                                "valueString": "4c26d6b9-8b1a-434e-b7d9-877b2b4fc15d"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/cb34a18d-35a1-4efb-8df2-0ad7c9ba3c4a"
            }
        },
        {
            "resource": {
                "resourceType": "ServiceRequest",
                "id": "7c566a82-c278-4df0-a49f-d1301fc10ac2",
                "basedOn": [
                    {
                        "reference": "CarePlan/323218c5-c445-40f9-abf3-72e1cf5d7f3e"
                    }
                ],
                "status": "active",
                "code": {
                    "text": "From Within Facility",
                    "coding": [
                        {
                            "display": "Internal facility referral or transfer",
                            "system": "http://loinc.org",
                            "code": "LA9328-1"
                        }
                    ]
                },
                "locationCode": [
                    {
                        "text": "My City"
                    }
                ],
                "intent": "plan",
                "subject": {
                    "reference": "Patient/f865c03b-2b85-4b1f-8d0f-9e7ef2039273"
                }
            },
            "request": {
                "method": "PUT",
                "url": "ServiceRequest/7c566a82-c278-4df0-a49f-d1301fc10ac2"
            }
        },
        {
            "resource": {
                "resourceType": "RelatedPerson",
                "id": "0398321e-12e0-4559-9729-d22bfd5eee0b",
                "patient": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "relationship": [
                    {
                        "text": "other"
                    },
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v3-RoleCode",
                                "code": "FAMMEMB"
                            }
                        ]
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Doe"
                        ]
                    }
                ],
                "gender": "female",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "0398321e-12e0-4559-9729-d22bfd5eee0b"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "8addd5dc-cd12-4b44-b844-d5fa4aaa4380"
                    }
                ],
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/fbict-registration-date",
                        "valueDateTime": "1986-05-10"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "RelatedPerson/0398321e-12e0-4559-9729-d22bfd5eee0b"
            }
        },
        {
            "resource": {
                "resourceType": "Patient",
                "id": "554bbe75-a55f-43ce-a8be-bcaccfefede4",
                "extension": [
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-religion",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/ValueSet/v3-ReligiousAffiliation",
                                    "code": "1036",
                                    "display": "Orthodox"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/patient-relatedPerson",
                        "valueReference": {
                            "reference": "RelatedPerson/0398321e-12e0-4559-9729-d22bfd5eee0b"
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/EducationalLevel",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://terminology.hl7.org/CodeSystem/v3-EducationLevel",
                                    "code": "ELEM",
                                    "display": "Elementary School"
                                }
                            ]
                        }
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/Occupation",
                        "valueString": "Foreman"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/SmartCareID",
                        "value": "554bbe75-a55f-43ce-a8be-bcaccfefede4"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/MRN",
                        "value": "MRN-554bbe75-a55f-43ce-a8be-bcaccfefede4"
                    },
                    {
                        "system": "http://cdr.aacahb.gov.et/UAN",
                        "value": "UAN-554bbe75-a55f-43ce-a8be-bcaccfefede4"
                    }
                ],
                "name": [
                    {
                        "use": "official",
                        "family": "Doe",
                        "given": [
                            "Jhon"
                        ]
                    }
                ],
                "telecom": [
                    {
                        "system": "phone",
                        "value": "+2519000000",
                        "use": "home"
                    }
                ],
                "gender": "male",
                "birthDate": "2021-12-31T22:00:00.000Z",
                "address": [
                    {
                        "type": "physical",
                        "text": "Urban",
                        "state": "Addis Ababa",
                        "city": "Cherkos sub city",
                        "district": "10",
                        "line": [
                            "17",
                            "927/5"
                        ]
                    }
                ],
                "maritalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-MaritalStatus",
                            "code": "M",
                            "display": "Married"
                        }
                    ]
                },
                "managingOrganization": {
                    "reference": "Organization/009a6a861c1b45778c0cbedadefe52a4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "5965138d-5f46-4e50-8a68-b3a5e849d3d7",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/care-plan",
                                "code": "hiv-positive-tracking",
                                "display": "HIV Positive Tracking"
                            }
                        ]
                    }
                ],
                "status": "active",
                "intent": "order",
                "created": "2020-10-23",
                "period": {
                    "start": "1988-09-30",
                    "end": "2020-09-13"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "supportingInfo": {
                    "reference": "ServiceRequest/0661ec2a-7d46-4d84-965c-c44aa2bd8008"
                },
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "started-art",
                                        "display": "Started ART"
                                    }
                                ]
                            },
                            "status": "not-started",
                            "statusReason": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking/status-reason",
                                        "code": "on-adherence-preparation"
                                    }
                                ]
                            },
                            "description": "Address adherence barriers"
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "linked-to-care",
                                        "display": "Linked to care and treatment"
                                    }
                                ]
                            },
                            "status": "not-started",
                            "scheduledPeriod": {
                                "start": "2008-06-20"
                            }
                        }
                    },
                    {
                        "extension": [
                            {
                                "url": "http://cdr.aacahb.gov.et/FinalOutcomeKnown",
                                "valueBoolean": true
                            }
                        ],
                        "outcomeCodeableConcept": [
                            {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/final-outcome",
                                        "code": "started-art-in-other-hf",
                                        "display": "Started ART in other HF"
                                    }
                                ]
                            }
                        ],
                        "detail": {
                            "code": {
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/tracking",
                                        "code": "final-outcome",
                                        "display": "Final Outcome"
                                    }
                                ]
                            },
                            "kind": "ServiceRequest",
                            "location": {
                                "display": "Teklehaymanot medium clinic"
                            },
                            "scheduledPeriod": {
                                "start": "2005-03-29"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/5965138d-5f46-4e50-8a68-b3a5e849d3d7"
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "6f2a95c9-5ca7-4e5d-a920-a10cece6fd7a",
                "activity": [
                    {
                        "detail": {
                            "code": {
                                "text": "Cryotherapy",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/precancerous-treatment",
                                        "code": "cryotherapy",
                                        "display": "Cryotherapy"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "precancerous lesion",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "285636001",
                                            "display": "Cervical intraepithelial neoplasia"
                                        }
                                    ]
                                }
                            ]
                        }
                    },
                    {
                        "detail": {
                            "code": {
                                "text": "Treated at the facility",
                                "coding": [
                                    {
                                        "system": "http://cdr.aacahb.gov.et/suspicious-cancerous-treatment",
                                        "code": "treated-at-facility",
                                        "display": "Treated at the facility"
                                    }
                                ]
                            },
                            "reasonReference": [
                                {
                                    "reference": "Observation/cda6fef003e74a548374d5f2ecea5a19"
                                }
                            ],
                            "scheduledPeriod": {
                                "start": "2020-10-20"
                            },
                            "status": "completed",
                            "reasonCode": [
                                {
                                    "text": "Suspected cervical cancer",
                                    "coding": [
                                        {
                                            "system": "http://snomed.info/sct",
                                            "code": "315266007",
                                            "display": "Suspected cervical cancer"
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ],
                "status": "completed",
                "category": [
                    {
                        "text": "Cervical cancer care plan",
                        "coding": [
                            {
                                "code": "cervical-cancer-care-plan",
                                "system": "http://cdr.aacahb.gov.et/cervical-cancer-care-plan",
                                "display": "Cervical cancer care plan"
                            }
                        ]
                    }
                ],
                "extension": [
                    {
                        "valueDateTime": "2025-05-16",
                        "url": "http://cdr.aacahb.gov.et/next-appintment-date"
                    }
                ],
                "intent": "order",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                }
            },
            "request": {
                "method": "PUT",
                "url": "CarePlan/6f2a95c9-5ca7-4e5d-a920-a10cece6fd7a"
            }
        },
        {
            "resource": {
                "resourceType": "DiagnosticReport",
                "id": "0019d388-4b8b-4733-8056-d9652c02e13d",
                "status": "final",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/v2-0074",
                                "code": "LAB",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "viral load"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "effectivePeriod": {
                    "start": "2022-05-29",
                    "end": "2020-07-11"
                },
                "conclusion": "Suppressed"
            },
            "request": {
                "method": "PUT",
                "url": "DiagnosticReport/0019d388-4b8b-4733-8056-d9652c02e13d"
            }
        },
        {
            "resource": {
                "resourceType": "Encounter",
                "id": "3b3d6118-e046-4159-af5a-c9f6fad164ae",
                "status": "finished",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/visit-type",
                        "valueString": "Scheduled"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/next-visit",
                        "valueDateTime": "1989-07-04"
                    }
                ],
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Encounter",
                        "value": "900326"
                    }
                ],
                "type": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "390906007"
                            }
                        ],
                        "text": "Follow-up encounter"
                    }
                ],
                "serviceType": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/service-type",
                            "code": "536",
                            "display": "Art therapy"
                        },
                        {
                            "system": "http://snomed.info/sct",
                            "code": "65153003",
                            "display": "Art therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "period": {
                    "start": "2020-07-15",
                    "end": "2004-02-12"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationDispense",
                "id": "a66e6030-4e16-4d45-b4ef-164cb14fbcee",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/was-switched",
                        "valueBoolean": true
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-type",
                        "valueString": "1st switch"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/switch-reason",
                        "valueString": "Clinical failure"
                    },
                    {
                        "url": "http://cdr.aacahb.gov.et/dose-end-date",
                        "valueDateTime": "1991-06-02"
                    }
                ],
                "status": "completed",
                "statusReasonCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/medication-dispense/status-reason",
                            "code": "restart"
                        }
                    ]
                },
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://cdr.aacahb.gov.et/hiv-regimen-codes",
                            "code": "2h"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "quantity": {
                    "value": 141,
                    "system": "http://terminology.hl7.org/CodeSystem/v3-orderableDrugForm",
                    "code": "Tablet",
                    "unit": "Tablet"
                },
                "daysSupply": {
                    "value": 179,
                    "unit": "Day",
                    "system": "http://unitsofmeasure.org",
                    "code": "d"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationDispense/a66e6030-4e16-4d45-b4ef-164cb14fbcee"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "f9931ed0-61eb-45fd-a7cd-6c9028e8fa7a",
                "status": "not-taken",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "effectivePeriod": {
                    "start": "2009-01-17"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/arv-therapy",
                                "code": "arv-treatment",
                                "display": "ARV Treatment started"
                            }
                        ],
                        "text": "ARV Treatment started"
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/f9931ed0-61eb-45fd-a7cd-6c9028e8fa7a"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "e0024dc1-096a-4e10-98e7-04200d9f7429",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "INH1"
                    }
                ],
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "status": "active",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "699618001",
                            "display": "Tuberculosis preventive therapy"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "effectivePeriod": {
                    "start": "2002-03-31",
                    "end": "2001-02-20"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://cdr.aacahb.gov.et/prophylaxis-type",
                                "code": "inh"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/e0024dc1-096a-4e10-98e7-04200d9f7429"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "aec3c626-2b65-49b9-9e42-1f83b4995bbf",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/TreatmentPhase",
                        "valueString": "TBRx1"
                    }
                ],
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "status": "stopped",
                "category": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "tb-treatment",
                            "display": "TB Treatment"
                        }
                    ]
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "effectivePeriod": {
                    "start": "1988-10-09",
                    "end": "2020-04-25"
                },
                "reasonCode": [
                    {
                        "coding": [
                            {
                                "system": "http://snomed.info/sct",
                                "code": "56717001",
                                "display": "Tuberculosis (disorder)"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/aec3c626-2b65-49b9-9e42-1f83b4995bbf"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "29882cd2-101a-4b0b-818a-139f629f1703",
                "extension": [
                    {
                        "url": "http://cdr.aacahb.gov.et/Adherence-level",
                        "valueString": "good"
                    }
                ],
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "398731002",
                            "display": "Product containing sulfamethoxazole and trimethoprim"
                        }
                    ],
                    "text": "Co-trimoxazole"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "effectivePeriod": {
                    "start": "1995-04-17",
                    "end": "2017-12-04"
                },
                "dosage": [
                    {
                        "maxDosePerPeriod": {
                            "numerator": {
                                "value": 30,
                                "unit": "Dose",
                                "system": "http://unitsofmeasure.org",
                                "code": "Dose"
                            },
                            "denominator": {
                                "value": 30,
                                "unit": "days",
                                "system": "http://unitsofmeasure.org",
                                "code": "d"
                            }
                        }
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/29882cd2-101a-4b0b-818a-139f629f1703"
            }
        },
        {
            "resource": {
                "resourceType": "MedicationStatement",
                "id": "423e6683-8441-42ef-b062-fe60e0f85df1",
                "context": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "status": "active",
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "387174006",
                            "display": "Fluconazole"
                        }
                    ],
                    "text": "Fluconazole"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "effectivePeriod": {
                    "start": "2016-04-03",
                    "end": "1989-10-31"
                }
            },
            "request": {
                "method": "PUT",
                "url": "MedicationStatement/423e6683-8441-42ef-b062-fe60e0f85df1"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "5ec99255-8783-47d9-8984-118e99836675",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "partOf": [
                    {
                        "reference": "MedicationDispense/a66e6030-4e16-4d45-b4ef-164cb14fbcee"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "418633004",
                            "display": "Medication adherence"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "135818000",
                            "display": "Poor - grade"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/5ec99255-8783-47d9-8984-118e99836675"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "a4b98f04-0ec0-44a8-abef-6fbfb3696353",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "social-history",
                                "display": "Social History"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "87276001",
                            "display": "Nutritional status"
                        }
                    ]
                },
                "valueCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "238131007",
                            "display": "Overweight"
                        }
                    ]
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/a4b98f04-0ec0-44a8-abef-6fbfb3696353"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "a684b2eb-5338-4f50-af52-7418adfe25ca",
                "status": "final",
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "vital-signs",
                                "display": "Vital Signs"
                            }
                        ],
                        "text": "Vital Signs"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://loinc.org",
                            "code": "29463-7",
                            "display": "Body weight"
                        }
                    ],
                    "text": "Weight"
                },
                "valueQuantity": {
                    "value": 114,
                    "unit": "kilogram",
                    "system": "http://unitsofmeasure.org",
                    "code": "kg"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/a684b2eb-5338-4f50-af52-7418adfe25ca"
            }
        },
        {
            "resource": {
                "resourceType": "Observation",
                "id": "58e819f1-2a83-40bd-9c33-0409983338b1",
                "status": "final",
                "identifier": [
                    {
                        "system": "http://cdr.aacahb.gov.et/Laoratory",
                        "value": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                    }
                ],
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/observation-category",
                                "code": "laboratory",
                                "display": "Laboratory"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "315124004",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ],
                    "text": "Viral load count"
                },
                "valueQuantity": {
                    "value": 90,
                    "unit": "Count",
                    "system": "http://unitsofmeasure.org",
                    "code": "{Count}"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Observation/58e819f1-2a83-40bd-9c33-0409983338b1"
            }
        },
        {
            "resource": {
                "id": "c6f18b4c-0f25-4b03-8621-31da37817e1e",
                "resourceType": "Procedure",
                "status": "completed",
                "category": {
                    "text": "Screening",
                    "coding": [
                        {
                            "code": "20135006",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "Cervical cancer screening",
                    "coding": [
                        {
                            "code": "243877001",
                            "system": "http://snomed.info/sct",
                            "display": "Cancer cervix screening status"
                        }
                    ]
                },
                "performedDateTime": "1996-03-09",
                "extension": [
                    {
                        "valueString": "Post-treatment follow-up screening",
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/c6f18b4c-0f25-4b03-8621-31da37817e1e"
            }
        },
        {
            "resource": {
                "id": "9ba8705e-3257-4f7f-91fe-33425da1e1cb",
                "resourceType": "Procedure",
                "status": "completed",
                "category": {
                    "text": "Laboratory procedure",
                    "coding": [
                        {
                            "code": "108252007",
                            "system": "http://snomed.info/sct"
                        }
                    ]
                },
                "code": {
                    "text": "viral load",
                    "coding": [
                        {
                            "code": "315124004",
                            "system": "http://snomed.info/sct",
                            "display": "Human immunodeficiency virus viral load"
                        }
                    ]
                },
                "report": [
                    {
                        "reference": "DiagnosticReport/cc71ecc72acf4f7f9a1b14dc3bc10767"
                    }
                ],
                "extension": [
                    {
                        "valueString": "Routine",
                        "url": "http://hl7.org/fhir/StructureDefinition/procedure-method"
                    }
                ],
                "reasonCode": [
                    {
                        "text": "Annual VL Test"
                    }
                ],
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                }
            },
            "request": {
                "method": "PUT",
                "url": "Procedure/9ba8705e-3257-4f7f-91fe-33425da1e1cb"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "3af6190f-42ef-472c-8001-b03178b5a351",
                "questionnaire": "PregnancyStatus",
                "status": "completed",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "item": [
                    {
                        "linkId": "pregnant",
                        "text": "Is Pregnant",
                        "answer": [
                            {
                                "valueBoolean": false,
                                "item": [
                                    {
                                        "linkId": "pregnant.want-to-be-pregnant",
                                        "text": "Want to be pregnant",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "is-breast-feeding",
                        "text": "Is breast feeding",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/3af6190f-42ef-472c-8001-b03178b5a351"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "ce9db337-67cd-4ad5-bc42-c99a25245d6c",
                "questionnaire": "ARTEligibility",
                "status": "completed",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "source": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "item": [
                    {
                        "linkId": "hiv-confirmation-date",
                        "text": "HIV Confirmed Date",
                        "answer": [
                            {
                                "valueDate": "1994-03-02"
                            }
                        ]
                    },
                    {
                        "linkId": "eligbility",
                        "item": [
                            {
                                "linkId": "eligbility.eligbile",
                                "text": "Eligible for ART",
                                "answer": [
                                    {
                                        "valueBoolean": true,
                                        "item": [
                                            {
                                                "linkId": "eligbility.eligbile.why",
                                                "text": "Why Eligible",
                                                "answer": [
                                                    {
                                                        "valueString": "Transfer In"
                                                    }
                                                ]
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/ce9db337-67cd-4ad5-bc42-c99a25245d6c"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "ed1c6bf0-2af3-48dc-81a5-4c19d8a82f85",
                "questionnaire": "AppointmentSpacingModel",
                "status": "completed",
                "encounter": {
                    "reference": "Encounter/3b3d6118-e046-4159-af5a-c9f6fad164ae"
                },
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "item": [
                    {
                        "linkId": "assessment",
                        "item": [
                            {
                                "linkId": "assessment.assessed",
                                "text": "Assessed For ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "assessment.date",
                                "text": "Assessed Date",
                                "answer": [
                                    {
                                        "valueBoolean": [
                                            false
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "category",
                        "text": "Category",
                        "answer": [
                            {
                                "valueString": "Category 4e"
                            }
                        ]
                    },
                    {
                        "linkId": "eligible",
                        "text": "Is Eligible For ASM",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "counseled",
                        "text": "Counseled",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "enrollment",
                        "item": [
                            {
                                "linkId": "enrollment.agree",
                                "text": "Agree To Be Enrolled",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.enrolled",
                                "text": "Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.reason",
                                "text": "Reason Not Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueString": "Disclosure Problem"
                                    }
                                ]
                            },
                            {
                                "linkId": "enrollment.date",
                                "text": "Enrollment Date",
                                "answer": [
                                    {
                                        "valueDate": "1989-06-15"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "couple-enrollment",
                        "item": [
                            {
                                "linkId": "couple-enrollment.enrolled",
                                "text": "Couple Enrolled To ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "couple-enrollment.uat-no",
                                "text": "Couple UAT No",
                                "answer": [
                                    {
                                        "valueString": "f6c3903f-d816-4c5c-b3ed-f346158cfb4a"
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "new-category-change",
                        "item": [
                            {
                                "linkId": "new-category-change.type",
                                "text": "New Category Change",
                                "answer": [
                                    {
                                        "valueBoolean": [
                                            false
                                        ]
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.reason",
                                "text": "Reason For Category Change",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "new-category-change.date",
                                "text": "Category Change Date",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "termination",
                        "item": [
                            {
                                "linkId": "termination.terminated",
                                "text": "Terminated From ASM",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.reason",
                                "text": "Reason For Termination",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            },
                            {
                                "linkId": "termination.date",
                                "text": "Terminated Date",
                                "answer": [
                                    {
                                        "valueBoolean": false
                                    }
                                ]
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/ed1c6bf0-2af3-48dc-81a5-4c19d8a82f85"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "14e0412a-4958-4200-adee-2ac8bd8abded",
                "questionnaire": "IndexCaseContactScreening",
                "status": "completed",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "item": [
                    {
                        "linkId": "screening-date",
                        "text": "Follow Up Date",
                        "answer": [
                            {
                                "valueDate": "1992-03-17"
                            }
                        ]
                    },
                    {
                        "linkId": "client-eligible",
                        "text": "Is the client eligible for Partner and Family Based ICT?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "newly-enrolled",
                        "text": "Is the client newly enrolled (Diagnosed)",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "high-viral-load",
                        "text": "Is the client with high viral load (HVL) (2>1000c/ml)?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "restart",
                        "text": "Is the client drop and return (Restart)?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "new-partner",
                        "text": "Is the client with new partner?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "sti-care",
                        "text": "Has the client in care with STI?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-disclosed",
                        "text": "Is the client with partner not yet disclosed?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "partner-not-tested",
                        "text": "Is the client with partner not tested?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "client-child-not-tested",
                        "text": "Is the client child (<15 years) not tested?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "kp-client",
                        "text": "Is the kp (FSW)?",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "maternal-hiv-status",
                        "text": "Maternal HIV status?",
                        "answer": [
                            {
                                "valueString": "Unknown status & alive"
                            }
                        ]
                    },
                    {
                        "linkId": "marital-status",
                        "text": "Marital status?",
                        "answer": [
                            {
                                "valueString": "Single"
                            }
                        ]
                    },
                    {
                        "linkId": "fbict-service",
                        "text": "Is the client (index case) offered with partner FBICT service?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "offer-accepted",
                        "text": "Has the client accepted the offer?",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contacts-elicited",
                        "text": "Number of contacts elicited?",
                        "answer": [
                            {
                                "valueString": 2
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/14e0412a-4958-4200-adee-2ac8bd8abded"
            }
        },
        {
            "resource": {
                "resourceType": "QuestionnaireResponse",
                "id": "548828fd-2c97-44fc-ad33-c072265e6810",
                "questionnaire": "IndexCaseFamilyContact",
                "status": "completed",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                },
                "source": {
                    "reference": "RelatedPerson/0398321e-12e0-4559-9729-d22bfd5eee0b"
                },
                "item": [
                    {
                        "linkId": "contact-prev-tested",
                        "text": "Contact previously been tested",
                        "answer": [
                            {
                                "valueBoolean": false,
                                "item": [
                                    {
                                        "linkId": "contact-prev-tested.date",
                                        "text": "Previous date tested",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-prev-tested.result",
                                        "text": "Previous HIV test result",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "contact-counseled",
                        "text": "Is the contact counseled for HIV today",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "hiv-care-linked",
                        "text": "Linked to HIV care",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "contact-tested",
                        "text": "Has the contact tested for HIV",
                        "answer": [
                            {
                                "valueBoolean": true,
                                "item": [
                                    {
                                        "linkId": "contact-tested.date",
                                        "text": "Date tested",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    },
                                    {
                                        "linkId": "contact-tested.result",
                                        "text": "HIV test result",
                                        "answer": [
                                            {
                                                "valueBoolean": false
                                            }
                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "linkId": "not-testing-reason",
                        "text": "Reason for not testing",
                        "answer": [
                            {
                                "valueString": "Refused"
                            }
                        ]
                    },
                    {
                        "linkId": "partner-started-art",
                        "text": "Has the partner started ART",
                        "answer": [
                            {
                                "valueBoolean": false
                            }
                        ]
                    },
                    {
                        "linkId": "client-health-status",
                        "text": "Health status of the client",
                        "answer": [
                            {
                                "valueString": "Healthy"
                            }
                        ]
                    },
                    {
                        "linkId": "living-with-index",
                        "text": "Currently living with index case",
                        "answer": [
                            {
                                "valueBoolean": true
                            }
                        ]
                    },
                    {
                        "linkId": "contact-mrn",
                        "text": "Contact MRN",
                        "answer": [
                            {
                                "valueString": "2b4aaf94-69c4-47de-ae2c-5db41a25346f"
                            }
                        ]
                    },
                    {
                        "linkId": "contact-uan",
                        "text": "Contact UAN",
                        "answer": [
                            {
                                "valueString": "1ed358ad-3349-4540-b2b4-8f1ad94569dd"
                            }
                        ]
                    }
                ]
            },
            "request": {
                "method": "PUT",
                "url": "QuestionnaireResponse/548828fd-2c97-44fc-ad33-c072265e6810"
            }
        },
        {
            "resource": {
                "resourceType": "ServiceRequest",
                "id": "0661ec2a-7d46-4d84-965c-c44aa2bd8008",
                "basedOn": [
                    {
                        "reference": "CarePlan/5965138d-5f46-4e50-8a68-b3a5e849d3d7"
                    }
                ],
                "status": "active",
                "code": {
                    "text": "From Within Facility",
                    "coding": [
                        {
                            "display": "Internal facility referral or transfer",
                            "system": "http://loinc.org",
                            "code": "LA9328-1"
                        }
                    ]
                },
                "locationCode": [
                    {
                        "text": "My City"
                    }
                ],
                "intent": "plan",
                "subject": {
                    "reference": "Patient/554bbe75-a55f-43ce-a8be-bcaccfefede4"
                }
            },
            "request": {
                "method": "PUT",
                "url": "ServiceRequest/0661ec2a-7d46-4d84-965c-c44aa2bd8008"
            }
        }
    ]
}
```
