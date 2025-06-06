## API Report File for "@backstage/plugin-catalog-backend-module-gitlab"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { BackendFeature } from '@backstage/backend-plugin-api';
import { CatalogProcessor } from '@backstage/plugin-catalog-node';
import { CatalogProcessorEmit } from '@backstage/plugin-catalog-node';
import { Config } from '@backstage/config';
import { EntityProvider } from '@backstage/plugin-catalog-node';
import { EntityProviderConnection } from '@backstage/plugin-catalog-node';
import { EventsService } from '@backstage/plugin-events-node';
import { GitLabIntegrationConfig } from '@backstage/integration';
import { GroupEntity } from '@backstage/catalog-model';
import { LocationSpec } from '@backstage/plugin-catalog-node';
import { LoggerService } from '@backstage/backend-plugin-api';
import { SchedulerService } from '@backstage/backend-plugin-api';
import { SchedulerServiceTaskRunner } from '@backstage/backend-plugin-api';
import { SchedulerServiceTaskScheduleDefinition } from '@backstage/backend-plugin-api';
import { UserEntity } from '@backstage/catalog-model';

// @public
const catalogModuleGitlabDiscoveryEntityProvider: BackendFeature;
export default catalogModuleGitlabDiscoveryEntityProvider;

// @public
export class GitlabDiscoveryEntityProvider implements EntityProvider {
  // (undocumented)
  connect(connection: EntityProviderConnection): Promise<void>;
  // (undocumented)
  static fromConfig(
    config: Config,
    options: {
      logger: LoggerService;
      events?: EventsService;
      schedule?: SchedulerServiceTaskRunner;
      scheduler?: SchedulerService;
    },
  ): GitlabDiscoveryEntityProvider[];
  // (undocumented)
  getProviderName(): string;
  refresh(logger: LoggerService): Promise<void>;
}

// @public
export class GitLabDiscoveryProcessor implements CatalogProcessor {
  // (undocumented)
  static fromConfig(
    config: Config,
    options: {
      logger: LoggerService;
      skipReposWithoutExactFileMatch?: boolean;
      skipForkedRepos?: boolean;
      includeArchivedRepos?: boolean;
    },
  ): GitLabDiscoveryProcessor;
  // (undocumented)
  getProcessorName(): string;
  // (undocumented)
  readLocation(
    location: LocationSpec,
    _optional: boolean,
    emit: CatalogProcessorEmit,
  ): Promise<boolean>;
}

// @public
export type GitLabGroup = {
  id: number;
  name: string;
  full_path: string;
  description?: string;
  visibility?: string;
  parent_id?: number;
};

// @public (undocumented)
export type GitLabGroupSamlIdentity = {
  extern_uid: string;
};

// @public
export class GitlabOrgDiscoveryEntityProvider implements EntityProvider {
  // (undocumented)
  connect(connection: EntityProviderConnection): Promise<void>;
  // (undocumented)
  static fromConfig(
    config: Config,
    options: {
      logger: LoggerService;
      events?: EventsService;
      schedule?: SchedulerServiceTaskRunner;
      scheduler?: SchedulerService;
      userTransformer?: UserTransformer;
      groupEntitiesTransformer?: GroupTransformer;
      groupNameTransformer?: GroupNameTransformer;
    },
  ): GitlabOrgDiscoveryEntityProvider[];
  // (undocumented)
  getProviderName(): string;
}

// @public
export type GitlabProviderConfig = {
  host: string;
  group: string;
  restrictUsersToGroup?: boolean;
  id: string;
  branch?: string;
  fallbackBranch: string;
  catalogFile: string;
  projectPattern: RegExp;
  userPattern: RegExp;
  groupPattern: RegExp;
  groupPatterns: RegExp[];
  allowInherited?: boolean;
  relations?: string[];
  orgEnabled?: boolean;
  schedule?: SchedulerServiceTaskScheduleDefinition;
  skipForkedRepos?: boolean;
  includeArchivedRepos?: boolean;
  excludeRepos?: string[];
  includeUsersWithoutSeat?: boolean;
  membership?: boolean;
  topics?: string;
};

// @public
export type GitLabUser = {
  id: number;
  username: string;
  email?: string;
  name: string;
  state: string;
  web_url: string;
  avatar_url: string;
  groups?: GitLabGroup[];
  group_saml_identity?: GitLabGroupSamlIdentity;
  is_using_seat?: boolean;
};

// @public
export type GroupNameTransformer = (
  options: GroupNameTransformerOptions,
) => string;

// @public
export interface GroupNameTransformerOptions {
  // (undocumented)
  group: GitLabGroup;
  // (undocumented)
  providerConfig: GitlabProviderConfig;
}

// @public
export type GroupTransformer = (
  options: GroupTransformerOptions,
) => GroupEntity[];

// @public
export interface GroupTransformerOptions {
  // (undocumented)
  groupNameTransformer: GroupNameTransformer;
  // (undocumented)
  groups: GitLabGroup[];
  // (undocumented)
  providerConfig: GitlabProviderConfig;
}

// @public
export type UserTransformer = (options: UserTransformerOptions) => UserEntity;

// @public
export interface UserTransformerOptions {
  // (undocumented)
  groupNameTransformer: GroupNameTransformer;
  // (undocumented)
  integrationConfig: GitLabIntegrationConfig;
  // (undocumented)
  providerConfig: GitlabProviderConfig;
  // (undocumented)
  user: GitLabUser;
}
```
