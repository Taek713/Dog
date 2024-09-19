# Doggos
import React from "react"
import { graphql } from "gatsby"
import Layout from "../components/layout"

const HomePage = ({ data }) => {
  const { dogs } = data

  return (
    <Layout>
      <h1>Dog Site!</h1>
      <p>There are many doggos waiting for their homes. Browse available dogs below:</p>
      <ul>
        {dogs.edges.map(({ node }) => (
          <li key={node.id}>
            <h2>{node.name}</h2>
            <img src={node.image.url} alt={node.name} />
            <p>{node.description}</p>
            <button>Adopt {node.name}</button>
          </li>
        ))}
      </ul>
    </Layout>
  )
}

export const query = graphql`
  query HomePageQuery {
    dogs: allDog {
      edges {
        node {
          id
          name
          image {
            url
          }
          description
        }
      }
    }
  }
`

export default HomePage
