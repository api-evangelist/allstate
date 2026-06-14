# Allstate Insurance GraphQL Schema

## Overview

This conceptual GraphQL schema models the core domain of Allstate Insurance, one of the largest publicly held personal lines property and casualty insurers in the United States. Allstate offers auto, home, life, renters, condo, motorcycle, boat, and business insurance products through a network of agents and digital channels.

This schema covers the full lifecycle of insurance operations: quoting, policy management, coverage configuration, driver and vehicle tracking, telematics (Drivewise), claims handling, repair coordination, and agent location.

## Source

- Provider: Allstate Insurance
- Website: https://www.allstate.com/
- GitHub Organization: https://github.com/Allstate
- LinkedIn: https://www.linkedin.com/company/allstate

## Schema File

See `allstate-schema.graphql` for the full type definitions.

## Top-Level Types

### Policy Types
- `Policy` — base policy with common fields shared across all policy lines
- `AutoPolicy` — automobile insurance policy with linked drivers and vehicles
- `HomePolicy` — homeowners insurance policy covering dwelling and personal property
- `LifePolicy` — life insurance policy with beneficiary and coverage amount
- `RentersPolicy` — renters insurance for tenants covering personal property and liability
- `CondoPolicy` — condominium unit owners policy
- `MotorcyclePolicy` — motorcycle insurance policy
- `BoatPolicy` — watercraft insurance policy
- `BusinessPolicy` — commercial/small business insurance policy
- `PolicyTerms` — effective dates, renewal terms, and billing cycle

### Policyholder and Insured
- `PolicyHolder` — the named account owner responsible for premium payments
- `NamedInsured` — person(s) listed on the policy declarations page
- `AdditionalInsured` — parties added to a policy with limited insured status

### Driver and Vehicle
- `Driver` — licensed driver associated with an auto or motorcycle policy
- `Vehicle` — insured vehicle linked to an auto or motorcycle policy
- `VehicleInfo` — make, model, year, trim, and usage classification
- `VIN` — parsed Vehicle Identification Number with decoded attributes
- `MVRRecord` — Motor Vehicle Record showing violations and license status
- `DriveHistory` — historical driving record and incident summary

### Coverage Types
- `Coverage` — base coverage type with limit, deductible, and premium
- `AutoCoverage` — aggregate auto coverages on a policy
- `BodilyInjury` — per-person and per-occurrence bodily injury liability limits
- `PropertyDamage` — property damage liability coverage
- `Collision` — collision coverage with deductible
- `Comprehensive` — comprehensive (other than collision) coverage
- `UninsuredMotorist` — coverage for accidents with uninsured drivers
- `UnderinsuredMotorist` — coverage when at-fault driver has insufficient limits
- `MedicalPayments` — medical payments coverage (MedPay)
- `RentalCoverage` — rental car reimbursement coverage
- `TowingCoverage` — roadside assistance and towing coverage
- `HomeCoverage` — aggregate home coverages on a homeowners policy

### Home Structure Coverages
- `Dwelling` — Coverage A: the main structure of the home
- `OtherStructures` — Coverage B: detached structures on the property
- `PersonalProperty` — Coverage C: personal belongings and contents
- `LossOfUse` — Coverage D: additional living expenses during repair
- `PersonalLiability` — Coverage E: personal liability protection
- `GuestMedical` — Coverage F: medical payments to guests

### Pricing and Discounts
- `Deductible` — deductible amount and type for a coverage
- `Premium` — premium breakdown including base, fees, and taxes
- `RateQuote` — rate quotation with expiration and binding instructions
- `Discount` — applied discount with code, name, and amount
- `SafeDriver` — safe driver discount eligibility and tier
- `MultiplePolicy` — multi-policy (bundling) discount details

### Telematics (Drivewise)
- `Drivewise` — Allstate Drivewise telematics program enrollment
- `DrivewiseScore` — composite driving score from telematics data
- `TripReport` — individual trip recorded by the Drivewise program
- `MilesDriven` — odometer and mileage tracking for usage-based insurance

### Claims
- `Claim` — insurance claim with status, date of loss, and coverage lines
- `ClaimNumber` — unique claim identifier and filing metadata
- `ClaimStatus` — current claim status and workflow stage
- `ClaimEstimate` — damage estimate and repair cost breakdown
- `ClaimPayment` — payment issued for a claim settlement
- `Adjuster` — assigned claims adjuster with contact information

### Repair and Rental
- `Repair` — repair order associated with a claim
- `GoodHandsRepair` — Allstate Good Hands Repair Network shop details
- `Rental` — rental vehicle arrangement during a covered repair

### Distribution and Auth
- `Agent` — licensed Allstate insurance agent with contact and license info
- `AgentLocator` — geographic search results for nearby agents
- `APIKey` — API key credential for programmatic access
- `Token` — OAuth 2.0 access token with scope and expiry

## Query Capabilities

- Fetch a policy by ID across all lines of business
- Look up a policyholder and their associated policies
- Retrieve coverage details and limits for any policy
- Get a rate quote for auto or home insurance
- View Drivewise enrollment status and trip history
- Look up claim status and payment history
- Find nearby agents by zip code or coordinates

## Mutation Capabilities

- Initiate a new quote request
- Bind a policy from an approved quote
- Add or remove a driver or vehicle from an auto policy
- Update coverage limits or deductibles
- File a new claim
- Upload claim documentation
- Enroll in Drivewise telematics

## Notes

This is a conceptual schema based on Allstate's publicly documented insurance products, coverage offerings, and digital capabilities. It is intended to illustrate how Allstate's domain model could be represented in a GraphQL API surface. Actual internal or partner API schemas may differ.
