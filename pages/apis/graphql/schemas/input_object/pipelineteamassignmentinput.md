---
#  _____   ____    _   _  ____ _______   ______ _____ _____ _______
#  |  __  / __   |  | |/ __ __   __| |  ____|  __ _   _|__   __|
#  | |  | | |  | | |  | | |  | | | |    | |__  | |  | || |    | |
#  | |  | | |  | | | . ` | |  | | | |    |  __| | |  | || |    | |
#  | |__| | |__| | | |  | |__| | | |    | |____| |__| || |_   | |
#  |_____/ ____/  |_| _|____/  |_|    |______|_____/_____|  |_|
#  This file is auto-generated by script/generate_graphql_api_content.sh,
#  please build the schema.graphql by running `rails graphql:update_reference_schema`
#  with https://github.com/buildkite/buildkite/,
#  replace the content in data/schema.graphql
#  and run the generation script `./scripts/generate-graphql-api-content.sh`.

title: PipelineTeamAssignmentInput – Input_objects – GraphQL API
toc: false
---
<!-- vale off -->
<h1 class="has-pills" data-algolia-exclude>
  PipelineTeamAssignmentInput
  <span class="pill pill--input_object pill--normal-case pill--large"><code>INPUT_OBJECT</code></span>
</h1>
<!-- vale on -->


Used to assign teams to pipelines



<table class="responsive-table responsive-table--single-column-rows">
  <thead>
    <th>
      <h2 data-algolia-exclude>Input Fields</h2>
    </th>
  </thead>
  <tbody>
    <tr><td><p><strong><code>accessLevel</code></strong><a href="/docs/apis/graphql/schemas/enum/pipelineaccesslevels" class="pill pill--enum pill--normal-case pill--medium" title="Go to ENUM PipelineAccessLevels"><code>PipelineAccessLevels</code></a></p><p>The access level members within the team have to the pipeline</p><p>Default value: MANAGE_BUILD_AND_READ</p></td></tr><tr><td><p><strong><code>id</code></strong><a href="/docs/apis/graphql/schemas/scalar/id" class="pill pill--scalar pill--normal-case pill--medium" title="Go to SCALAR ID"><code>ID!</code></a></p><p>The ID of the team you want to be assigned</p></td></tr>
  </tbody>
</table>
