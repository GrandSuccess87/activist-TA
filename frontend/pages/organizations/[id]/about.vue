<template>
  <div
    class="px-4 xl:px-8 flex flex-col text-light-text dark:text-dark-text bg-light-content dark:bg-dark-content"
  >
    <Head>
      <Title>{{ organization.name }}</Title>
    </Head>
    <PageBreadcrumbs class="mt-4" :organization="organization" />
    <h1
      class="pt-6 font-bold transition-all duration-500 responsive-h1 text-light-text dark:text-dark-text"
    >
      {{ organization.name }}
    </h1>
    <flex class="relative flex items-center w-full py-6"
      ><h2
        :v-if="organization.tagline"
        class="transition-all duration-500 responsive-h4 text-light-special-text dark:text-dark-special-text"
      >
        {{ organization.tagline }}
      </h2>
      <div class="absolute right-0 flex space-x-3">
        <BtnLabeled
          :cta="true"
          linkTo="/"
          label="Support"
          fontSize="base"
          leftIcon="IconSupport"
          iconSize="1.25em"
          :counter="organization.supporters"
        />
        <BtnLabeled
          :cta="true"
          linkTo="/"
          label="Share organization"
          fontSize="base"
          leftIcon="bi:box-arrow-up"
          iconSize="1.25em"
        />
      </div>
    </flex>
    <div class="pb-6 space-y-6">
      <div class="flex">
        <CardAbout
          aboutType="organization"
          :organization="organization"
          class="w-[73%]"
        />
        <div class="w-[2%]"></div>
        <div class="w-[25%] h-fill">
          <MediaImageCarousel />
        </div>
      </div>
      <CardGetInvolved :organization="organization" />
      <CardConnect
        :social-links="organization.socialLinks"
        :userIsAdmin="true"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
const { id } = useRoute().params;

definePageMeta({
  layout: "sidebar",
});

import { Organization } from "~~/types/organization";

const organization: Organization = {
  name: "tech from below",
  tagline: "Technologie von und für soziale Bewegungen",
  location: "Berlin, Germany",
  description:
    "Nulla aliqua sit fugiat commodo excepteur deserunt dolor ullamco Lorem. Esse aliquip nisi ullamco pariatur velit officia. Eiusmod commodo nulla consequat minim laboris pariatur adipisicing. Veniam amet nostrud id cupidatat. Esse duis velit elit duis non labore adipisicing sunt eu nostrud. Occaecat mollit et do consectetur fugiat amet.",
  topic: "Technology and Privacy",
  members: 3,
  supporters: 60,
  imageURL: "/images/tech-from-below.svg",
  workingGroups: ["meetup", "code-night"],
  socialLinks: ["tfb@mastodon", "tfb@email"],
};
</script>