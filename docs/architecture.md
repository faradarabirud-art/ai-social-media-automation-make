# Workflow Architecture

## Overview

This project uses Make.com as the orchestration platform for an AI-powered social media content generation and publishing workflow.

The automation begins when a new row is detected in Google Sheets. The topic is researched using Perplexity AI, transformed into platform-specific content using OpenAI, and paired with an AI-generated image from Leonardo AI.

The generated data is written back to Google Sheets before the workflow branches into Facebook and LinkedIn publishing routes.

## Workflow Diagram

```text
Google Sheets - Watch New Rows
        |
        v
Perplexity AI - Research & Summarize
        |
        v
OpenAI - Generate Facebook Post
        |
        v
OpenAI - Generate LinkedIn Post
        |
        v
OpenAI - Generate Image Prompt
        |
        v
Leonardo AI - Generate Image
        |
        v
Google Sheets - Update Row
        |
        v
      Router
      /    \
     /      \
    v        v
Facebook   HTTP - Download Image
Pages             |
                  v
              LinkedIn
