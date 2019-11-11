---
layout: twoColumn
section: resources
type: article
title:  Webhook Events
description: A webhook is an action that occurs within the Dwolla platform and is delivered via a webhook to notify a third-party application of the occurrence of the event.

samples:
    customerCreated: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/a6f09251-c2de-4833-94a8-5c70916cebbc",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/a6f09251-c2de-4833-94a8-5c70916cebbc",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/29a82d20-a703-41cb-9b3c-bd409c499925",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-05-30T18:21:11.490Z",
          "id": "29a82d20-a703-41cb-9b3c-bd409c499925",
          "resourceId": "a6f09251-c2de-4833-94a8-5c70916cebbc",
          "topic": "customer_created"
        }

        ```

    customerReverificationNeeded: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/15b9ecc2-0c83-4e85-bf9f-948458a8be63",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/15b9ecc2-0c83-4e85-bf9f-948458a8be63",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/b5f4179e-840e-4b63-b148-ea18cb80b9a7",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-05-29T16:39:49.847Z",
          "id": "b5f4179e-840e-4b63-b148-ea18cb80b9a7",
          "resourceId": "15b9ecc2-0c83-4e85-bf9f-948458a8be63",
          "topic": "customer_reverification_needed"
        }

        ```

    customerKbaVerificationNeeded: >
        ```jsonnoselect

        {
          "_links": {
              "self": {
                "href": "https://api-sandbox.dwolla.com/events/36c99d4e-ec2f-4a31-8318-2f39121dc6dc",
                "type": "application/vnd.dwolla.v1.hal+json",
                "resource-type": "event"
              },
              "resource": {
                "href": "https://api-sandbox.dwolla.com/customers/5da64ab9-785e-4b67-96b1-7ab5f1a12e22",
                "type": "application/vnd.dwolla.v1.hal+json"
              },
              "account": {
                "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
                "type": "application/vnd.dwolla.v1.hal+json",
                "resource-type": "account"
              },
              "customer": {
                "href": "https://api-sandbox.dwolla.com/customers/5da64ab9-785e-4b67-96b1-7ab5f1a12e22",
                "type": "application/vnd.dwolla.v1.hal+json",
                "resource-type": "customer"
              }
          },
          "id": "36c99d4e-ec2f-4a31-8318-2f39121dc6dc",
          "created": "2019-10-30T15:39:23.560Z",
          "topic": "customer_kba_verification_needed",
          "resourceId": "5da64ab9-785e-4b67-96b1-7ab5f1a12e22"
        }

        ```

    customerKbaVerificationPassed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/e94951e3-6c83-40e2-990f-b25a76ce753e",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "event"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/5da64ab9-785e-4b67-96b1-7ab5f1a12e22",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "account"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/5da64ab9-785e-4b67-96b1-7ab5f1a12e22",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "customer"
            }
          },
          "id": "e94951e3-6c83-40e2-990f-b25a76ce753e",
          "created": "2019-10-30T15:40:02.379Z",
          "topic": "customer_kba_verification_passed",
          "resourceId": "5da64ab9-785e-4b67-96b1-7ab5f1a12e22"
        }

        ```

    customerKbaVerificationFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/83602871-b142-47cb-a5d6-ddf240416955",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "event"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/a811608d-140a-4e2c-9eed-ee26dd5172b0",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "account"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/a811608d-140a-4e2c-9eed-ee26dd5172b0",
              "type": "application/vnd.dwolla.v1.hal+json",
              "resource-type": "customer"
            }
          },
          "id": "83602871-b142-47cb-a5d6-ddf240416955",
          "created": "2019-10-30T15:43:26.256Z",
          "topic": "customer_kba_verification_failed",
          "resourceId": "a811608d-140a-4e2c-9eed-ee26dd5172b0"
        }

        ```

    customerVerificationDocumentNeeded: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/02749a08-068b-43a2-b792-c7cf8762f226",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-05-30T18:27:24.860Z",
          "id": "02749a08-068b-43a2-b792-c7cf8762f226",
          "resourceId": "4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
          "topic": "customer_verification_document_needed"
        }

        ```

    customerVerificationDocumentUploaded: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/e878da16-5d04-4285-b5e9-6d5b8ac4418a"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/e6f84583-543e-438e-9db3-f9127f985fa5"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/5701dc20-8fd7-449e-bf66-5b5e1f04608d"
            }
          },
          "created": "2017-01-21T17:09:49.860Z",
          "id": "e878da16-5d04-4285-b5e9-6d5b8ac4418a",
          "resourceId": "e6f84583-543e-438e-9db3-f9127f985fa5",
          "topic": "customer_verification_document_uploaded"
        }

        ```

    customerVerificationDocumentFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/6d89da24-ca10-496b-bd3c-7e24ba1f6562"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/e6f84583-543e-438e-9db3-f9127f985fa5"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/5701dc20-8fd7-449e-bf66-5b5e1f04608d"
            }
          },
          "created": "2017-01-21T17:12:41.177Z",
          "id": "6d89da24-ca10-496b-bd3c-7e24ba1f6562",
          "resourceId": "e6f84583-543e-438e-9db3-f9127f985fa5",
          "topic": "customer_verification_document_failed"
        }

        ```

    customerVerificationDocumentApproved: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/aa4ebc7b-e3d0-4f1d-98e9-5a67620fdc3b"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/e6f84583-543e-438e-9db3-f9127f985fa5"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/5701dc20-8fd7-449e-bf66-5b5e1f04608d"
            }
          },
          "created": "2017-01-21T17:16:21.723Z",
          "id": "aa4ebc7b-e3d0-4f1d-98e9-5a67620fdc3b",
          "resourceId": "e6f84583-543e-438e-9db3-f9127f985fa5",
          "topic": "customer_verification_document_approved"
        }

        ```

    customerVerified: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/7a48e039-f004-409a-b43a-fcce65ccd76a",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-05-30T18:38:18.397Z",
          "id": "7a48e039-f004-409a-b43a-fcce65ccd76a",
          "resourceId": "4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
          "topic": "customer_verified"
        }

        ```

    customerSuspended: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/9c949341-653e-41f3-a27c-00c772e41061"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "created": "2017-01-20T22:10:39.309Z",
          "id": "9c949341-653e-41f3-a27c-00c772e41061",
          "resourceId": "e358a488-6699-4d79-bbfb-c5bf58100ea4",
          "topic": "customer_suspended"
        }

        ```

    customerActivated: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/0f0ab172-0800-42a7-86d4-768661861cea"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "created": "2017-01-20T22:11:58.983Z",
          "id": "0f0ab172-0800-42a7-86d4-768661861cea",
          "resourceId": "e358a488-6699-4d79-bbfb-c5bf58100ea4",
          "topic": "customer_activated"
        }

        ```

    customerDeactivated: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/3dfa3922-c873-4d2e-a3de-ab80bb8ac67e"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/customers/be2d2322-fdee-4361-8722-4289f5601604"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/be2d2322-fdee-4361-8722-4289f5601604"
            }
          },
          "created": "2017-07-24T14:51:56.932Z",
          "id": "3dfa3922-c873-4d2e-a3de-ab80bb8ac67e",
          "resourceId": "be2d2322-fdee-4361-8722-4289f5601604",
          "topic": "customer_deactivated"
        }

        ```

    customerBeneficialOwnerCreated: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/beneficial-owners/41cb879c-bd00-4afd-aa6c-03c2b7ced158",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/6d4a51b9-2503-4b17-bc28-beb6ea722556",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "6d4a51b9-2503-4b17-bc28-beb6ea722556",
          "resourceId": "41cb879c-bd00-4afd-aa6c-03c2b7ced158",
          "topic": "customer_beneficial_owner_created",
          "created": "2019-05-30T21:38:28.483Z"
        }

        ```

    customerBeneficialOwnerRemoved: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/beneficial-owners/41cb879c-bd00-4afd-aa6c-03c2b7ced158",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/7f9ebdea-457b-e911-8119-d7bc0de34d9c",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "7f9ebdea-457b-e911-8119-d7bc0de34d9c",
          "resourceId": "41cb879c-bd00-4afd-aa6c-03c2b7ced158",
          "topic": "customer_beneficial_owner_removed",
          "created": "2019-05-30T21:38:28.483Z"
        }

        ```

    customerBeneficialOwnerVerified: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/beneficial-owners/41cb879c-bd00-4afd-aa6c-03c2b7ced158",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/dc6fc216-2911-4378-81a8-279f2c81e49a",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "dc6fc216-2911-4378-81a8-279f2c81e49a",
          "resourceId": "41cb879c-bd00-4afd-aa6c-03c2b7ced158",
          "topic": "customer_beneficial_owner_verified",
          "created": "2019-05-30T21:38:28.483Z"
        }


        ```

    customerBeneficialOwnerVerificationDocumentNeeded: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/beneficial-owners/3898c437-539b-4af4-b608-af62c9b344c1",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/f28c9580-4d80-47bf-b8cc-2b1808cfd1eb",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "f28c9580-4d80-47bf-b8cc-2b1808cfd1eb",
          "resourceId": "3898c437-539b-4af4-b608-af62c9b344c1",
          "topic": "customer_beneficial_owner_verification_document_needed",
          "created": "2019-05-30T21:42:57.019Z"
        }

        ```

    customerBeneficialOwnerVerificationDocumentUploaded: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/cc71ecaa-de89-4108-8dba-b62c264a31af",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/fd999c53-2695-4626-bd16-7bd009530dfd",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-06-06T18:20:24.065Z",
          "id": "fd999c53-2695-4626-bd16-7bd009530dfd",
          "resourceId": "cc71ecaa-de89-4108-8dba-b62c264a31af",
          "topic": "customer_beneficial_owner_verification_document_uploaded"
        }

        ```

    customerBeneficialOwnerVerificationDocumentFailed: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/d6500f93-70a3-49c9-a5dd-a51708cd29bb",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/a51d185f-347e-48d7-9f1f-7d007e498768",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-06-06T18:21:38.070Z",
          "id": "a51d185f-347e-48d7-9f1f-7d007e498768",
          "resourceId": "d6500f93-70a3-49c9-a5dd-a51708cd29bb",
          "topic": "customer_beneficial_owner_verification_document_failed"
        }

        ```

    customerBeneficialOwnerVerificationDocumentApproved: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/documents/d2fa0201-cc33-487f-b5d9-13b4fcfa6375",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/864661ec-5760-46f6-861d-a95b3ecc1666",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "created": "2019-06-06T18:22:44.659Z",
          "id": "864661ec-5760-46f6-861d-a95b3ecc1666",
          "resourceId": "d2fa0201-cc33-487f-b5d9-13b4fcfa6375",
          "topic": "customer_beneficial_owner_verification_document_approved"
        }

        ```

    customerBeneficialOwnerReverificationNeeded: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/ba295d5a-039c-4278-ac9e-0b0077226eeb",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/beneficial-owners/3898c437-539b-4af4-b608-af62c9b344c1",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/5c247d55-d94e-4a3d-8aa6-53307f20e1b6",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "5c247d55-d94e-4a3d-8aa6-53307f20e1b6",
          "resourceId": "3898c437-539b-4af4-b608-af62c9b344c1",
          "topic": "customer_beneficial_owner_reverification_needed",
          "created": "2019-05-30T21:48:49.889Z"
        }

        ```

    customerFundingSourceAdded: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/84f296e9-08a6-46b2-bb23-bd25552492f5"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "84f296e9-08a6-46b2-bb23-bd25552492f5",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_funding_source_added",
          "created": "2017-01-20T22:15:48.265Z"
        }

        ```

    customerFundingSourceRemoved: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/f8fef3b4-4d6a-4c10-94f4-2a11b4791b6a"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "f8fef3b4-4d6a-4c10-94f4-2a11b4791b6a",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_funding_source_removed",
          "created": "2017-01-20T22:26:25.973Z"
        }

        ```

    customerFundingSourceVerified: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/55886d20-e242-4f4d-b75f-f23851363237"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "55886d20-e242-4f4d-b75f-f23851363237",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_funding_source_verified",
          "created": "2017-01-20T22:23:42.928Z"
        }

        ```

    customerFundingSourceUnverified: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/e2906820-d687-4201-98c2-055eb218fc22"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "e2906820-d687-4201-98c2-055eb218fc22",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_funding_source_unverified",
          "created": "2017-01-20T22:26:25.973Z"
        }

        ```

    customerFundingSourceNegative: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/da9de3aa-2fc9-46dc-9d5e-5055d1910e2c"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "da9de3aa-2fc9-46dc-9d5e-5055d1910e2c",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_funding_source_negative",
          "created": "2017-01-20T22:26:25.973Z"
        }

        ```

    customerFundingSourceUpdated: >
        ```jsonnoselect

        {
          "_links": {
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
              "resource-type": "account",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/4e1ba3ba-4948-413e-a4f2-65def9c3d7e5",
              "resource-type": "customer",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/da9de3aa-2fc9-46dc-9d5e-5055d1910e2c",
              "type": "application/vnd.dwolla.v1.hal+json"
            },
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/c3b0db02-b4a7-463e-ba6c-34857bf8105f",
              "resource-type": "event",
              "type": "application/vnd.dwolla.v1.hal+json"
            }
          },
          "id": "c3b0db02-b4a7-463e-ba6c-34857bf8105f",
          "resourceId": "da9de3aa-2fc9-46dc-9d5e-5055d1910e2c",
          "topic": "customer_funding_source_updated",
          "created": "2019-05-30T21:29:29.317Z"
        }

        ```

    customerMicrodepositsAdded: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/d765519c-a43f-49b8-8124-082d752065eb"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "d765519c-a43f-49b8-8124-082d752065eb",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_microdeposits_added",
          "created": "2017-01-20T22:17:08.675Z"
        }

        ```

    customerMicrodepositsFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/f025832c-a0e6-4e2a-a8c1-bcc255fdc720"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/752fe4da-421e-4b4c-a422-48370d8a52a6"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "f025832c-a0e6-4e2a-a8c1-bcc255fdc720",
          "resourceId": "752fe4da-421e-4b4c-a422-48370d8a52a6",
          "topic": "customer_microdeposits_failed",
          "created": "2017-01-20T22:29:01.409Z"
        }

        ```

    customerMicrodepositsCompleted: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/6c9d289c-26af-4fc0-a227-2ca1345172fd"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "6c9d289c-26af-4fc0-a227-2ca1345172fd",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_microdeposits_completed",
          "created": "2017-01-20T22:21:21.328Z"
        }

        ```

    customerMicrodepositsMaxattempts: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/6c9d289c-26af-4fc0-a227-2ca1345172fd"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/funding-sources/00e17e13-8ebb-4160-96e7-c632170ef9f9"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "6c9d289c-26af-4fc0-a227-2ca1345172fd",
          "resourceId": "00e17e13-8ebb-4160-96e7-c632170ef9f9",
          "topic": "customer_microdeposits_maxattempts",
          "created": "2017-01-20T22:21:21.328Z"
        }

        ```

    customerBankTransferCreated: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/c6694e91-a425-4e69-819a-2e033e33df8a"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/98603beb-63df-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/491b1fff-514b-4d90-9a3f-4360a51ab47b"
            }
          },
          "id": "c6694e91-a425-4e69-819a-2e033e33df8a",
          "resourceId": "98603beb-63df-e611-80ee-0aa34a9b2388",
          "topic": "customer_bank_transfer_completed",
          "created": "2017-01-20T22:58:44.900Z"
        }

        ```

    customerBankTransferCancelled: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/9ae33508-1015-429c-ac14-ff05d29164b1"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/4e8d29e9-00e0-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/9bc9c1be-3546-46d7-b883-49be0a9b0df3"
            }
          },
          "id": "9ae33508-1015-429c-ac14-ff05d29164b1",
          "resourceId": "4e8d29e9-00e0-e611-80ee-0aa34a9b2388",
          "topic": "customer_bank_transfer_cancelled",
          "created": "2017-01-21T17:42:16.492Z"
        }

        ```

    customerBankTransferFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/eef9f3d0-ea9d-474d-8b68-fba5b54cfc04"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/55c89a4e-63df-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/491b1fff-514b-4d90-9a3f-4360a51ab47b"
            }
          },
          "id": "eef9f3d0-ea9d-474d-8b68-fba5b54cfc04",
          "resourceId": "55c89a4e-63df-e611-80ee-0aa34a9b2388",
          "topic": "customer_bank_transfer_failed",
          "created": "2017-01-20T22:53:47.421Z"
        }

        ```

    customerBankTransferCreationFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/c0b583dc-f7f2-4ac0-901f-e6f2e9ebbefc"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/bc78e0a3-01e0-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/9bc9c1be-3546-46d7-b883-49be0a9b0df3"
            }
          },
          "id": "c0b583dc-f7f2-4ac0-901f-e6f2e9ebbefc",
          "resourceId": "bc78e0a3-01e0-e611-80ee-0aa34a9b2388",
          "topic": "customer_bank_transfer_creation_failed",
          "created": "2017-01-21T17:47:59.932Z"
        }

        ```

    customerBankTransferCompleted: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/6822a340-b8c4-432a-ba71-9ae90cb70ec4"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/1e91b014-eedf-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/491b1fff-514b-4d90-9a3f-4360a51ab47b"
            }
          },
          "id": "6822a340-b8c4-432a-ba71-9ae90cb70ec4",
          "resourceId": "1e91b014-eedf-e611-80ee-0aa34a9b2388",
          "topic": "customer_bank_transfer_completed",
          "created": "2017-01-21T17:34:46.450Z"
        }

        ```

    customerTransferCreated: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/cac95329-9fa5-42f1-a4fc-c08af7b868fb"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/cdb5f11f-62df-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "cac95329-9fa5-42f1-a4fc-c08af7b868fb",
          "resourceId": "cdb5f11f-62df-e611-80ee-0aa34a9b2388",
          "topic": "customer_transfer_created",
          "created": "2017-01-20T22:45:12.790Z"
        }

        ```

    customerTransferCancelled: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/c3a889d4-9a79-4b41-a8ff-25fac33107e3"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/cdb5f11f-62df-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/491b1fff-514b-4d90-9a3f-4360a51ab47b"
            }
          },
          "id": "c3a889d4-9a79-4b41-a8ff-25fac33107e3",
          "resourceId": "cdb5f11f-62df-e611-80ee-0aa34a9b2388",
          "topic": "customer_transfer_cancelled",
          "created": "2017-01-20T22:48:07.552Z"
        }

        ```

    customerTransferFailed: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/eef9f3d0-ea9d-474d-8b68-fba5b54cfc04"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/55c89a4e-63df-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/491b1fff-514b-4d90-9a3f-4360a51ab47b"
            }
          },
          "id": "eef9f3d0-ea9d-474d-8b68-fba5b54cfc04",
          "resourceId": "55c89a4e-63df-e611-80ee-0aa34a9b2388",
          "topic": "customer_transfer_failed",
          "created": "2017-01-20T22:53:47.421Z"
        }

        ```

    customerTransferCompleted: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/ea7435f6-d7d6-4f14-9ed9-8602369d268b"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/transfers/52de20f1-eddf-e611-80ee-0aa34a9b2388"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/e358a488-6699-4d79-bbfb-c5bf58100ea4"
            }
          },
          "id": "ea7435f6-d7d6-4f14-9ed9-8602369d268b",
          "resourceId": "52de20f1-eddf-e611-80ee-0aa34a9b2388",
          "topic": "customer_transfer_completed",
          "created": "2017-01-21T15:27:07.438Z"
        }

        ```

    customerMassPaymentCreated: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/cc8ace67-e6ee-4963-84f1-1936c558418f"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/mass-payments/47ccaea8-6f7c-43b1-a368-a702012631c6"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/9bc9c1be-3546-46d7-b883-49be0a9b0df3"
            }
          },
          "id": "cc8ace67-e6ee-4963-84f1-1936c558418f",
          "resourceId": "47ccaea8-6f7c-43b1-a368-a702012631c6",
          "topic": "customer_mass_payment_created",
          "created": "2017-01-21T17:51:06.927Z"
        }

        ```

    customerMassPaymentCompleted: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/c036bcf7-6b76-482c-af32-71df7175e7a2"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/mass-payments/47ccaea8-6f7c-43b1-a368-a702012631c6"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/9bc9c1be-3546-46d7-b883-49be0a9b0df3"
            }
          },
          "id": "c036bcf7-6b76-482c-af32-71df7175e7a2",
          "resourceId": "47ccaea8-6f7c-43b1-a368-a702012631c6",
          "topic": "customer_mass_payment_completed",
          "created": "2017-01-21T17:51:08.305Z"
        }

        ```

    customerMassPaymentCancelled: >
        ```jsonnoselect

        {
          "_links": {
            "self": {
              "href": "https://api-sandbox.dwolla.com/events/bdb4fc57-c844-41d5-9553-9e8bfb00498d"
            },
            "account": {
              "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
            },
            "resource": {
              "href": "https://api-sandbox.dwolla.com/mass-payments/47ccaea8-6f7c-43b1-a368-a702012631c6"
            },
            "customer": {
              "href": "https://api-sandbox.dwolla.com/customers/9bc9c1be-3546-46d7-b883-49be0a9b0df3"
            }
          },
          "id": "bdb4fc57-c844-41d5-9553-9e8bfb00498d",
          "resourceId": "47ccaea8-6f7c-43b1-a368-a702012631c6",
          "topic": "customer_mass_payment_cancelled",
          "created": "2017-01-21T17:51:08.305Z"
        }

        ```

---

# Webhooks Events

When an action occurs within the Dwolla system on a resource (Customers, Transfers, etc.), an Event object is created to record a change to the state of the resource. All created Webhook Events follow the same format and include high level details such as: an event topic, a resource URL that identifies the specific resource that changed states, and a timestamp of when the event was created. If your application has an active [webhook subscription](https://developers.dwolla.com/guides/webhooks/create-subscription.html
), all Events relevant to your integration will trigger a webhook notification each time they occur. The following resource article will provide guidance on the structure of webhook events, which will assist with handling incoming webhooks.

**Note:** Dwolla **requires** all applications to have a created webhook subscription in production. The webhook subscription is used to notify your application to trigger an email notification to your end-users.

## Webhook request details

When your webhook subscription is configured, events will be created and sent asynchronously via webhooks as they occur. The webhook notification from Dwolla is a POST request that contains a JSON-encoded payload as well as HTTP headers, which are both used when consuming the webhook. Webhook payloads are designed to be lightweight with only minimum details regarding the triggered event. Dwolla returns links within the Event object pointing to relevant resources in the API which are used to lookup more detailed information on the resource that changed states.

## Webhook headers

There are a few HTTP headers that are useful for your application when consuming the webhook request. `x-dwolla-topic` lets your app know, at a high level, the type of event being sent in the payload. `x-request-signature-sha256` contains a HMAC SHA256 hash based on the  webhook payload and a key which is your webhook secret. The webhook signature should be [validated](https://developers.dwolla.com/guides/webhooks/validating-webhooks.html) prior to parsing the webhook payload.

+ `x-dwolla-topic` - customer_created
+ `x-request-signature-sha-256` - ed551cfb4acb48d31e14886bffa33aa417dfa4a3d3778f6141a7f7f92ee64861

## Webhook payload

All webhook payloads will include an Event object which will follow the same format as outlined in the [API reference docs](https://docs.dwolla.com/#events). An Event contains `_links` to: the relevant resource that caused the Event to be triggered, the Customer that the Event belongs to, and a `self` link to identify the unique Event. In addition to relevant `_links`, the payload will include attributes such as a created timestamp, event topic, and resourceId.

| Attribute  | Description                                |
|------------|--------------------------------------------|
| _links     | An object that contains relevant links to resources in the Dwolla API. Possible links can include: `self`, `account`, `resource`, and `customer`. <br> `self` -  a link to the unique event <br> `account` - a link to the Dwolla account that the application belongs to <br> `resource` - a link to the resource that changed states. Used to lookup additional details returned on the resource itself <br> `customer` - a link to the customer the Event belongs to |
| id         | Unique Event Id. An Event Id is used along with the created timestamp for idempotent event processing.                 |
| created    | ISO-8601 timestamp when event was created.          |
| topic      | Type of action that occurred with Dwolla.           |
| resourceId | Unique Id of the resource that triggered the Event. |

### Example Webhook payload

```jsonnoselect
{
  "_links": {
    "account": {
      "href": "https://api-sandbox.dwolla.com/accounts/0ee84069-47c5-455c-b425-633523291dc3",
      "resource-type": "account",
      "type": "application/vnd.dwolla.v1.hal+json"
    },
    "customer": {
      "href": "https://api-sandbox.dwolla.com/customers/a6f09251-c2de-4833-94a8-5c70916cebbc",
      "resource-type": "customer",
      "type": "application/vnd.dwolla.v1.hal+json"
    },
    "resource": {
      "href": "https://api-sandbox.dwolla.com/customers/a6f09251-c2de-4833-94a8-5c70916cebbc",
      "type": "application/vnd.dwolla.v1.hal+json"
    },
    "self": {
      "href": "https://api-sandbox.dwolla.com/events/29a82d20-a703-41cb-9b3c-bd409c499925",
      "resource-type": "event",
      "type": "application/vnd.dwolla.v1.hal+json"
    }
  },
  "created": "2019-05-30T18:21:11.490Z",
  "id": "29a82d20-a703-41cb-9b3c-bd409c499925",
  "resourceId": "a6f09251-c2de-4833-94a8-5c70916cebbc",
  "topic": "customer_created"
}
```

## List of supported events by resource

Webhooks are available for the list of Events shown below. As API enhancements are made, Dwolla may add new Events at any point in the future.

> **Note:** The Event topic for all events triggered for your end-users that are created as Customers will be prepended with `customer_*`. Events that represent actions being triggered on your primary Dwolla Account are not shown below. Refer to the [API docs](https://docs.dwolla.com/#events) for the complete list of Events.

### Customers

<table>
  <thead>
    <tr>
      <th>Event Topic Name</th>
      <th>Description</th>
    </tr>
  </thead>

  <tbody>

    <tr>
      <td>customer_created</td>
      <td><p><strong>Description</strong>: A Customer was created.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#create-a-customer">Create a Customer</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerCreated | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_reverification_needed</td>
      <td><p><strong>Description</strong>: Incomplete information was received for a Customer; updated information is needed to verify the Customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#update-a-customer">Update a Customer</a> endpoint, or when Dwolla  places a Customer into <code>retry</code> status.</p>
        <button class="accordion"></button>
          <div class="accordion-content">
            {{ page.samples.customerReverificationNeeded | markdownify }}
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_kba_verification_needed</td>
      <td><p><strong>Description</strong>: The <code>retry</code> verification attempt failed; additional knowledge-based authentication is needed from the customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#update-a-customer">Update a Customer</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerKbaVerificationNeeded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_kba_verification_failed</td>
      <td><p><strong>Description</strong>: The Customer failed to pass knowledge-based authentication.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#verify-kba-questions">Verify KBA questions</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerKbaVerificationFailed | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_kba_verification_passed</td>
      <td><p><strong>Description</strong>: The Customer successfully passed knowledge-based authentication.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#verify-kba-questions">Verify KBA questions</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerKbaVerificationPassed | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_needed</td>
      <td style="max-width:100px"><p><strong>Description</strong>: Additional documentation is needed to verify a Customer.</p>
      <p><strong>Timing</strong>: Occurs when a second attempt to re-verify a Customer fails, which systematically places the Customer in <code>document</code> status immediately after a POST request to the <a href="https://docs.dwolla.com/#update-a-customer">Update a Customer</a> endpoint.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerVerificationDocumentNeeded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_uploaded</td>
      <td><p><strong>Description</strong>: A verification document was uploaded for a Customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#create-a-document-for-a-customer">Create a Document</a> endpoint.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerVerificationDocumentUploaded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_failed</td>
      <td><p><strong>Description</strong>: A verification document was rejected for a Customer.</p>
      <p><strong>Timing</strong>: Occurs when a document uploaded for a Customer is reviewed by Dwolla, and rejected with a <a href="https://developers.dwolla.com/resources/business-verified-customer/handling-controller-and-customer-statuses.html#document-failure">document failure</a> reason, usually within 1-2 business days of uploading a document.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerVerificationDocumentFailed | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_approved</td>
      <td><p><strong>Description</strong>: A verification document was approved for a Customer.</p>
      <p><strong>Timing</strong>: Occurs when a document uploaded for a Customer is reviewed by Dwolla, and approved, usually within 1-2 business days of uploading a document.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerVerificationDocumentApproved | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verified</td>
      <td><p><strong>Description</strong>: A Customer was verified.</p>
      <p><strong>Timing</strong>: Occurs when a Customer is verified by Dwolla upon a POST request to the <a href="https://docs.dwolla.com/#create-a-customer">Create a Customer</a> endpoint. In a case where the Customer isn’t instantly verified upon creation, this event occurs when the Customer is verified after a <code>retry</code> attempt, or after a document is approved.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerVerified | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_suspended</td>
      <td><p><strong>Description</strong>: A Customer was suspended.</p>
      <p><strong>Timing</strong>: Occurs when Dwolla systematically places a Customer in <code>suspended</code> status as a result of uploading fraudulent document, or upon receiving certain <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html#list-of-possible-return-codes-descriptions-and-actions">ACH return codes</a> when a transfer fails.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerSuspended | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_activated</td>
      <td><p><strong>Description</strong>: A Customer moves from deactivated or suspended to an active status.</p>
      <p><strong>Timing</strong>: Occurs upon reactivating a Customer that has a <code>deactivated</code> status by making a POST request to the <a href="https://docs.dwolla.com/#update-a-customer">Update a Customer</a> endpoint, or when Dwolla reactivates a Customer that has a <code>suspended</code> status.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerActivated | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_deactivated</td>
      <td><p><strong>Description</strong>: A Customer was deactivated.</p>
      <p><strong>Timing</strong>: Occurs upon deactivation of a Customer by making a POST request to the <a href="https://docs.dwolla.com/#update-a-customer">Update a Customer</a> endpoint, or when Dwolla systematically deactivates a Customer upon receiving certain <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html#list-of-possible-return-codes-descriptions-and-actions">ACH return codes</a> when a transfer fails.</p>
      <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerActivated | markdownify }}
        </div>
      </td>
    </tr>

  </tbody>
</table>

### Customers - Beneficial Owners

<table>
  <thead>
    <tr>
      <th>Event Topic Name</th>
      <th>Description</th>
    </tr>
  </thead>

  <tbody>

    <tr>
      <td>customer_beneficial_owner_created</td>
      <td><p><strong>Description</strong>: A Beneficial owner was successfully created.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#create-a-beneficial-owner">Create a beneficial owner</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerCreated | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_beneficial_owner_removed</td>
      <td><p><strong>Description</strong>: An individual beneficial owner has been successfully removed from the Customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#remove-a-beneficial-owner">Remove a beneficial owner</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerRemoved | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_beneficial_owner_verification_document_needed</td>
      <td><p><strong>Description</strong>: Additional documentation is needed to verify an individual beneficial owner.</p>
      <p><strong>Timing</strong>: Occurs when a second attempt to re-verify a beneficial owner fails, which systematically places the beneficial owner in <code>document</code> status immediately after a POST request to the <a href="https://docs.dwolla.com/#update-a-beneficial-owner">Update a beneficial owner</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerVerificationDocumentNeeded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_beneficial_owner_verification_document_uploaded</td>
      <td><p><strong>Description</strong>: A verification document was uploaded for beneficial owner.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#create-a-document-for-a-beneficial-owner">Create a document for a beneficial owner</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerVerificationDocumentUploaded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_beneficial_owner_verification_document_failed</td>
      <td><p><strong>Description</strong>: A verification document was rejected for a beneficial owner.</p>
      <p><strong>Timing</strong>: Occurs when a document uploaded for a beneficial owner is reviewed by Dwolla, and rejected with a <a href="https://developers.dwolla.com/resources/business-verified-customer/handling-controller-and-customer-statuses.html#document-failure">document failure reason</a> reason, usually within 1-2 business of uploading a document.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerVerificationDocumentFailed | markdownify }}
        </div>
      </td>
    </tr>


    <tr>
      <td>customer_beneficial_owner_verification_document_approved</td>
      <td><p><strong>Description</strong>: A verification document was approved for a beneficial owner.</p>
      <p><strong>Timing</strong>: Occurs when a document uploaded for a Customer is reviewed by Dwolla, and approved, usually within 1-2 business days of uploading a document.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerVerificationDocumentApproved | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_beneficial_owner_reverification_needed</td>
      <td><p><strong>Description</strong>: A previously verified beneficial owner status has changed due to either a change in the beneficial owner’s information or at request for more information from Dwolla. The individual will need to verify their identity within 30 days.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#update-a-beneficial-owner">Update a beneficial owner</a> endpoint, or when Dwolla places the beneficial owner into <code>incomplete</code> status.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerBeneficialOwnerReverificationNeeded | markdownify }}
        </div>
      </td>
    </tr>

  </tbody>
</table>

### Customers - Funding Sources

<table>
  <thead>
    <tr>
      <th>Event Topic Name</th>
      <th>Description</th>
    </tr>
  </thead>

  <tbody>

    <tr>
      <td>customer_funding_source_added</td>
      <td><p><strong>Description</strong>: A funding source was added to a Customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#create-a-funding-source-for-a-customer">Create a funding source for a customer</a> endpoint, or when a funding source is added via <a href="https://developers.dwolla.com/resources/dwolla-js.html">dwolla.js</a> or a <a href="https://developers.dwolla.com/resources/funding-source-verification.html">third party bank verification method</a>.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceAdded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_removed</td>
      <td><p><strong>Description</strong>: A funding source was removed from a Customer.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#remove-a-funding-source">Remove a funding source</a> endpoint, or when Dwolla systematically removes a funding source upon receiving certain <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html#list-of-possible-return-codes-descriptions-and-actions">ACH return codes</a> when a transfer fails.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceRemoved | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_verified</td>
      <td><p><strong>Description</strong>: A Customer’s funding source was marked as verified.</p>
      <p><strong>Timing</strong>: Occurs upon a successful POST request to the <a href="https://docs.dwolla.com/#verify-micro-deposits">Verify micro-deposits</a> endpoint, or when a funding source is added + verified via <a href="https://developers.dwolla.com/resources/funding-source-verification/instant-account-verification.html">IAV</a> or a <a href="https://developers.dwolla.com/resources/funding-source-verification.html">third party bank verification method</a>. Also occurs in cases where Dwolla manually marks a funding source as <code>verified</code>.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceVerified | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_unverified</td>
      <td><p><strong>Description</strong>: A funding source has been systematically <code>unverified</code>. This is generally a result of a transfer failure. View our <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html">developer resource article</a> to learn more.</p>
      <p><strong>Timing</strong>: Occurs when Dwolla systematically marks a funding source <code>unverified</code> upon receiving certain <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html#list-of-possible-return-codes-descriptions-and-actions">ACH return codes</a> when a transfer fails.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceUnverified | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_negative</td>
      <td><p><strong>Description</strong>: A Customer’s <a href="https://developers.dwolla.com/resources/balance-funding-source.html">balance</a> has gone negative. You are responsible for ensuring a zero or positive Dwolla balance for Customer accounts created by your application. If a Customer’s Dwolla balance has gone negative, you are responsible for making the Dwolla Customer account whole. Dwolla will notify you via a webhook and separate email of the negative balance.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#initiate-a-transfer">Initiate a transfer</a> endpoint that causes a funding source balance to go negative.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceNegative | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_updated</td>
      <td><p><strong>Description</strong>: A Customer’s funding source has been updated. This can also be fired as a result of a correction after a bank transfer processes. For example, a financial institution can issue a correction to change the bank account <code>type</code> from <code>checking</code> to <code>savings</code>.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#update-a-funding-source">Update a funding source</a> endpoint.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerFundingSourceUpdated | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_micro_deposits_added</td>
      <td><p><strong>Description</strong>: Two less than or equal to ten cent transfers to a Customer’s linked bank account were initiated.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#initiate-micro-deposits">Initiate micro-deposits</a> endpoint, or when a Customer selects the <a href="https://developers.dwolla.com/resources/dwolla-js/instant-account-verification.html#options-and-customization"><code>microdeposits</code> option within IAV</a>.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerMicrodepositsAdded | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_micro_deposits_failed</td>
      <td><p><strong>Description</strong>: The two less than or equal to ten cent transfers to a Customer’s linked bank account failed to clear successfully.</p>
      <p><strong>Timing</strong>: Occurs when micro-deposits fails to clear into a bank account, usually within 1-2 business days of initiating them.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerMicrodepositsFailed | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_micro_deposits_completed</td>
      <td><p><strong>Description</strong>: The two less than or equal to ten cent transfers to a Customer’s linked bank account were successful.</p>
      <p><strong>Timing</strong>: Occurs when micro-deposit are successful, usually within 1-2 business days of initiating them.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerMicrodepositsFailed | markdownify }}
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_micro_deposits_maxattempts</td>
      <td><p><strong>Description</strong>: The Customer has reached their max verification attempts, limit of three. The Customer can no longer verify their funding source with the completed micro-deposit amounts.</p>
      <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#verify-micro-deposits">Verify micro-deposits</a> endpoint with incorrect micro-deposit amounts.</p>
        <button class="accordion"></button>
        <div class="accordion-content">
          {{ page.samples.customerMicrodepositsMaxattempts | markdownify }}
        </div>
      </td>
    </tr>

  </tbody>
</table>

### Customers - Transfers

<table>
  <thead>
    <tr>
      <th>Event Topic Name</th>
      <th>Description</th>
    </tr>
  </thead>

  <tbody>

  <tr>
    <td>customer_bank_transfer_created</td>
    <td><p><strong>Description</strong>: A bank transfer was created for a Customer. Represents funds moving either from a verified Customer’s bank to the Dwolla Platform or from the Dwolla Platform to a verified Customer’s bank.</p>
    <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#initiate-a-transfer">Initiate a transfer</a> endpoint when sending funds from a Verified Customer’s bank, or when funds move from a receiving Verified Customer’s <code>balance</code> to their bank.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerBankTransferCreated | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_bank_transfer_cancelled</td>
    <td><p><strong>Description</strong>: A pending Customer bank transfer has been cancelled, and will not process further. Represents a cancellation of funds either transferring from a verified Customer’s bank to the Dwolla Platform or from the Dwolla Platform to a verified Customer’s bank.</p>
    <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#cancel-a-transfer">Cancel a transfer</a> endpoint, or when Dwolla manually cancels a transfer.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerBankTransferCancelled | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_bank_transfer_failed</td>
    <td><p><strong>Description</strong>: A Customer bank transfer. Usually, this is a result of an ACH failure (insufficient funds, etc.). Represents a failed funds transfer either from a verified Customer’s bank to the Dwolla Platform or from the Dwolla Platform to a verified Customer’s bank.</p>
    <p><strong>Timing</strong>: Occurs when Dwolla marks a transfer as <code>failed</code>.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerBankTransferFailed | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_bank_transfer_creation_failed</td>
    <td><p><strong>Description</strong>: Transfers initiated to a verified Customer’s bank must pass through the verified Customer’s balance before being sent to a receiving bank. Dwolla will fail to create a transaction intended for a verified Customer’s bank if the funds available in the balance are less than the transfer amount.</p>
    <p><strong>Timing</strong>: Occurs when a transfer to a verified Customer’s bank fails to be created.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerBankTransferCreationFailed | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_bank_transfer_completed</td>
    <td><p><strong>Description</strong>: A bank transfer that was created for a Customer was success. Represents a successful funds transfer either from a verified Customer’s bank to the Dwolla Platform or from the Dwolla Platform to a verified Customer’s bank.</p>
    <p><strong>Timing</strong>: Occurs when a funds transfer into the Dwolla Platform or a verified Customer’s bank is successful, based on the <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/processing-times.html">transfer processing timing</a> used.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerBankTransferCompleted | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_transfer_created</td>
    <td><p><strong>Description</strong>: A transfer was created for a Customer. Represents funds transferring from a verified Customer’s balance or unverified Customer’s bank.</p>
    <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#initiate-a-transfer">Initiate a transfer</a> endpoint when sending funds from a verified Customer’s <code>balance</code>, or to/from an unverified Customer’s bank.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerTransferCreated | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_transfer_cancelled</td>
    <td><p><strong>Description</strong>: A pending transfer has been cancelled, and will not process further. Represents a cancellation of funds transferring either to an unverified Customer’s bank or to a verified Customer’s balance.</p>
    <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#cancel-a-transfer">Cancel a transfer</a> endpoint to cancel a transfer initiated from a verified Customer’s <code>balance</code>, or to/from an unverified Customer’s bank.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerTransferCancelled | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_transfer_failed</td>
    <td><p><strong>Description</strong>: A Customer transfer failed. Represents a failed funds transfer either to an unverified Customer’s bank or to a verified Customer’s balance.</p>
    <p><strong>Timing</strong>: Occurs when Dwolla marks a transfer as <code>failed</code>.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerTransferFailed | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_transfer_completed</td>
    <td><p><strong>Description</strong>: A Customer transfer was  successful. Represents a successful funds transfer either to an unverified Customer’s bank or to a verified Customer’s balance.</p>
    <p><strong>Timing</strong>: Occurs when a funds transfer into an unverified Customer’s bank or a verified Customer’s balance is successful, based on the <a href="https://developers.dwolla.com/resources/bank-transfer-workflow/processing-times.html">transfer processing timing</a> used.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerTransferCompleted | markdownify }}
      </div>
    </td>
  </tr>

  </tbody>
</table>

### Customers - Mass Payments

<table>
  <thead>
    <tr>
      <th>Event Topic Name</th>
      <th>Description</th>
    </tr>
  </thead>

  <tbody>

  <tr>
    <td>customer_mass_payment_created</td>
    <td><p><strong>Description</strong>: A verified Customer’s mass payment was created.</p>
     <p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#initiate-a-mass-payment">Initiate a mass-payment</a> endpoint.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerMassPaymentCreated | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_mass_payment_completed</td>
    <td><p><strong>Description</strong>: A verified Customer’s mass payment was completed. However, this doesn’t mean that each mass payment item’s transfer was  successful.</p>
    <p><strong>Timing</strong>: Occurs when a mass payment job completes.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerMassPaymentCompleted | markdownify }}
      </div>
    </td>
  </tr>

  <tr>
    <td>customer_mass_payment_cancelled</td>
    <td><p><strong>Description</strong>: A Verified Customer’s created and deferred mass payment was cancelled.</p><p><strong>Timing</strong>: Occurs upon a POST request to the <a href="https://docs.dwolla.com/#update-a-mass-payment">Update a mass-payment</a> endpoint when cancelling a mass payment job.</p>
      <button class="accordion"></button>
      <div class="accordion-content">
        {{ page.samples.customerMassPaymentCancelled | markdownify }}
      </div>
    </td>
  </tr>

  </tbody>
</table>
