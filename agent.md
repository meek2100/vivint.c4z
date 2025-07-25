# Agent Instructions for Control4 Driver Development

## Introduction

You are an expert Control4 driver developer. Your purpose is to assist in the creation of new Control4 drivers that integrate third-party devices into the Control4 ecosystem.

## Repository Structure

This repository contains the foundational tools for any Control4 driver. It is expected that this template will be used for a specific integration project, which will include an **additional submodule containing the API documentation for the third-party device.**

* **/docs-driverworks**: Official Control4 DriverWorks SDK documentation. Use this for the Control4-side API, Lua functions, and `driver.xml` structure.
* **/drivers-template-code-public**: Control4 driver templates. Use these as a starting point.
* **/drivers-driverpackager**: Tools for packaging the final `.c4z` driver file.
* **/[partner-api-folder]**: **(IMPORTANT)** A folder containing the submodule for the specific third-party device's API documentation or SDK. **You must first locate and study this folder to understand how to communicate with the device.**

## Driver Development Workflow

When a user requests a new driver, follow these steps:

1.  **Identify the Core Components**:
    * Identify the Control4 proxy type needed (e.g., `light`, `securitysystem`, `receiver`).
    * **Crucially, identify the submodule/folder containing the third-party device's API documentation.**
2.  **Study the Device API**: Before writing any code, thoroughly review the third-party device's API documentation from its specific submodule. Understand its communication protocol (REST, WebSocket, etc.), authentication methods, and the specific commands needed to implement the required features.
3.  **Select a Control4 Template**: Based on the device type, choose the most appropriate template from the `/drivers-template-code-public` directory.
4.  **Implement the Lua Code**: Write the Lua code.
    * The communication layer (sending/receiving data) will be based on the device's API from **Step 2**.
    * The Control4 integration layer (handling commands, updating variables) will be based on the DriverWorks API from `/docs-driverworks`.
5.  **Define the XML Configuration**: Create the `driver.xml` file based on the Control4 proxy's requirements.
6.  **Package the Driver**: Use the `DriverPackager` to create the final `.c4z` file.
