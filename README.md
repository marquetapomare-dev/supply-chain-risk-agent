# Supply Chain Capacity & Risk Agent

An AI-powered supply chain decision-support application built on Cloudflare that analyzes supplier capacity against demand, identifies capacity risk, and recommends mitigation actions.

## Overview

The Supply Chain Capacity & Risk Agent is designed to help supply chain professionals quickly evaluate capacity scenarios across multiple suppliers.

Users can enter demand and supplier capacity data through a conversational interface. The application calculates total available capacity, shortage or surplus, utilization, and overall capacity risk. The AI then interprets the results and provides a concise recommended action.

The agent also supports follow-up scenarios. Users can change an existing supplier's capacity and compare how that change affects overall supply risk without re-entering the entire scenario.

## Key Features

- Conversational AI interface for supply chain capacity analysis
- Multi-supplier capacity modeling
- Deterministic calculation of demand versus total capacity
- Shortage and surplus identification
- Capacity utilization calculation
- Supply risk assessment
- Recommended mitigation actions
- Conversational memory for follow-up capacity scenarios
- Before-and-after risk comparison

## Example

A user can provide the following scenario:

- Demand: 800 units
- Supplier Alpha: 300 units
- Supplier Beta: 250 units
- Supplier Gamma: 150 units

The agent calculates:

- Total Capacity: 700 units
- Shortage: 100 units
- Utilization: 114.3%
- Risk Status: Capacity Constraint

The user can then ask a follow-up question such as:

> Supplier Gamma can increase capacity by 150 units. How does that change the risk?

The agent retains the previous scenario, updates Supplier Gamma's capacity, recalculates the results, and explains the change in risk.

## Architecture

This application uses:

- Cloudflare Workers
- Cloudflare Workers AI
- Cloudflare Agents
- Durable Object-backed agent state
- React and TypeScript
- A custom `analyzeCapacity` tool for deterministic supply chain calculations

The AI model handles natural-language interaction and interpretation, while the custom capacity analysis tool performs the underlying mathematical calculations.

## AI Model

The application uses the Cloudflare Workers AI model:

`@cf/zai-org/glm-4.7-flash`

## Capacity Analysis Logic

The custom capacity tool calculates:

- Total supplier capacity
- Capacity shortage or surplus
- Capacity utilization
- Capacity risk status

This separates deterministic supply chain calculations from the language model's interpretation of the results.

## Conversational State

The agent maintains conversation context so users can perform scenario analysis through follow-up questions.

For example, after establishing an initial supplier capacity scenario, a user can increase one supplier's capacity and ask how the change affects overall risk. The agent uses the prior scenario, updates the changed value, and performs a new analysis.

## Running Locally

Install dependencies:

npm install

Start the development server:

npm run dev

Then open the local URL provided by the development server.

Cloudflare authentication is required for Workers AI.

## AI-Assisted Development

AI-assisted coding was used during development for application planning, implementation guidance, debugging, testing, and documentation.

A separate `PROMPT_HISTORY.md` file documents the AI-assisted development process and representative prompts used while building the application.