<template>
  <Layout>
    <div class="container">
      <Hero :theme="$page.theme.edges[0].node"/>
      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>

<page-query>
query{
  journals: allStrapiJournal{
    edges{
      node{
        title,
        id,
        created_at,
      }
    }
  }
  projects: allStrapiProject{
    edges{
      node{
        title,
        id,
        created_at,
        thumbnail{
          url
        },
        categories{
          id,
          title
        }
      }
    }
  },
  theme: allStrapiTheme{
    edges{
      node{
        hero_title,
        hero_subtitle,
        site_name,
        site_description,
        dark_mode
      }
    }
  }
}
</page-query>


<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  }
}
</script>
