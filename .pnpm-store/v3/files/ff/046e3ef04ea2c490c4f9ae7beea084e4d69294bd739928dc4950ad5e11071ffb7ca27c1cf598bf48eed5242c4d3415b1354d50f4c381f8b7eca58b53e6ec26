import { ClientDependenciesBuilder, ClientHeaderBuilder, ClientBuilder, QueryOptions } from '@orval/core';

declare const getSvelteQueryDependencies: ClientDependenciesBuilder;
declare const getReactQueryDependencies: ClientDependenciesBuilder;
declare const getVueQueryDependencies: ClientDependenciesBuilder;
declare const generateQueryHeader: ClientHeaderBuilder;
declare const generateQuery: ClientBuilder;
declare const builder: ({ type, options: queryOptions, }?: {
    type?: "react-query" | "vue-query" | "svelte-query" | undefined;
    options?: QueryOptions | undefined;
}) => () => {
    client: ClientBuilder;
    header: ClientHeaderBuilder;
    dependencies: ClientDependenciesBuilder;
};

export { builder, builder as default, generateQuery, generateQueryHeader, getReactQueryDependencies, getSvelteQueryDependencies, getVueQueryDependencies };
