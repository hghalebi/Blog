# Aegis Quick Start

Production configuration for agents with a single decorator.

Aegis is a deployment layer that surrounds your existing agent functions with a protective shield. You keep your logic exactly as it is. Aegis handles all production concerns - compute, routing, scaling, authentication, and observability - automatically.

> "Do not worry, I will protect your service and take care of everything."

---

## Quickstart

### Step 1: Installation

Install the Aegis deployment library and the core agent SDK.

```bash
pip install aegis-deploy agents pydantic


⸻

Step 2: Project Structure

Aegis requires a minimal configuration file at your project root to handle environment-level settings.

my-project/
├── app.py          # Your agent code
└── aegis.toml      # Project configuration

aegis.toml:

[env]
OPENAI_API_KEY = "env:OPENAI_API_KEY"

[azure]
region = "westeurope"
resource_group = "aegis-guardrails"


⸻

Step 3: Write your Agent

Aegis attaches a deployment aura to your function. Your function remains pure and agent-oriented, while Aegis takes care of the infrastructure.

Below is the transformation from a local script to a production service.

Local Agent Function
Standard Open Agent SDK code.

from agents import GuardrailFunctionOutput, Agent, Runner
from pydantic import BaseModel


class HomeworkOutput(BaseModel):
    is_homework: bool
    reasoning: str


guardrail_agent = Agent(
    name="Guardrail check",
    instructions="Check if the user is asking about homework.",
    output_type=HomeworkOutput,
)


async def homework_guardrail(ctx, agent, input_data):
    result = await Runner.run(guardrail_agent, input_data, context=ctx.context)
    final_output = result.final_output_as(HomeworkOutput)
    return GuardrailFunctionOutput(
        output_info=final_output,
        tripwire_triggered=not final_output.is_homework,
    )

Production Service
Ready for deployment with one decorator.

from aegis_deploy import aegis
from agents import GuardrailFunctionOutput, Agent, Runner
from pydantic import BaseModel


class HomeworkOutput(BaseModel):
    is_homework: bool
    reasoning: str


guardrail_agent = Agent(
    name="Guardrail check",
    instructions="Check if the user is asking about homework.",
    output_type=HomeworkOutput,
)


@aegis.azure(
    name="homework-guardrail",
    route="/guardrails/homework",
    region="westeurope",
    compute="standard.cpu.xs",
    auth="bearer",
    scale={"min": 1, "max": 5},
    timeout=15,
    env=["OPENAI_API_KEY"],
)
async def homework_guardrail(ctx, agent, input_data):
    """
    Aegis automatically injects the production context and handles
    HTTP request parsing before this function is hit.
    """
    result = await Runner.run(guardrail_agent, input_data, context=ctx.context)
    final_output = result.final_output_as(HomeworkOutput)

    return GuardrailFunctionOutput(
        output_info=final_output,
        tripwire_triggered=not final_output.is_homework,
    )

The decorator expresses production configuration, not business logic.

⸻

Step 4: Deploy

Deploying is a single command. Aegis parses your decorators, builds the container, registers routes, and provisions resources.

aegis deploy azure

Output:

⠋ Analyzing dependency graph…
⠙ Provisioning Azure Resources (West Europe)…
✓ Service homework-guardrail active.
Endpoint: https://api.aegis.cloud/guardrails/homework

⸻

Features

Deployment Primitives

Aegis maps decorator parameters directly to cloud infrastructure primitives. You never touch containers, Terraform, or YAML.

Primitive	Description
name	The unique identifier for the service.
route	The public HTTP endpoint path.
compute	Abstracted resource envelope (for example standard.cpu.xs).
region	The physical cloud location for deployment.
auth	The access policy (for example bearer, public).
timeout	Execution SLA in seconds.
scale	Autoscaling boundaries (min and max).


⸻

Local Development

You can simulate the full production environment locally.

aegis dev

This spins up an HTTP server that mirrors the exact routes and auth behavior you will have in production.

⸻

Observability

Aegis injects a protected context into ctx. You get logging, metrics, and tracing out of the box.

# Inside your agent function
ctx.log.info("Evaluating guardrail call")
ctx.metrics.increment("guardrail.homework.requests")

All logs are automatically exported to your cloud provider’s observability suite.

