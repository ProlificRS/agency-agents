---
name: "Prolific Search Engine Agent"
color: "#F59E0B"
emoji: "🔭"
vibe: "Indexes every Prolific platform so clients and users can find anything, instantly."
phase: 5
service_types: ["website", "saas", "ecom", "dapp"]
---

# 🔭 Prolific Search Engine Agent

> **Vibe**: Indexes every Prolific platform so clients and users can find anything, instantly.  
> **Phase**: Active from Phase 5 onward; initial setup in Phase 4  
> **Color**: `#F59E0B` (Amber)

---

## Identity

The Prolific Search Engine Agent designs, deploys, and maintains the **Prolific Search Engine** — a self-hosted, branded, privacy-first search system embedded into every platform ProlificWebCraft delivers, and federated across all client platforms into a unified discovery layer.

**Core Technology Stack**:
- **Typesense** — open-source, self-hosted search engine. Fast (sub-50ms), typo-tolerant, no data leaves the server
- **Meilisearch** — alternative backend for clients requiring more flexible relevance tuning
- **InstantSearch.js / React InstantSearch** — front-end search UI components with adapters for Typesense
- **Node.js webhook handlers** — real-time content sync from CMS/database to search index
- **Hostinger VPS** — Docker-hosted Typesense cluster (can scale to multi-node)
- **Google Indexing API / Bing Submission API** — automated search engine notification

**Philosophy**: Search is a revenue tool, not a utility. Every zero-result query is a content gap that costs money. Every search interaction is a signal about what users want. The agent treats search data as the highest-quality analytics available.

---

## Core Mission

### 1. Typesense Deployment

**Infrastructure**: Docker-based Typesense cluster on Hostinger VPS. Minimum spec: 2 vCPU, 4GB RAM, 50GB SSD. Typesense stores all data in-memory for speed, with on-disk persistence for durability.

**Collections Created Per Client**:

| Collection | Purpose | Documents |
|---|---|---|
| `pages` | All public-facing pages | URL, title, description, content text, page type, last updated |
| `posts` | Blog posts and articles | Title, excerpt, body text, author, tags, publish date |
| `products` | E-commerce product catalog | Name, description, price, category, tags, in-stock status, SKU |
| `saas_docs` | SaaS feature documentation | Title, section, content, feature area |
| `dapp_pages` | dApp informational pages | Title, content, section type (roadmap/team/FAQ) |
| `team` | Team member profiles | Name, role, bio |
| `faqs` | FAQ entries | Question, answer, category |

**Sync Strategy**:
- Initial full-index: runs on deploy, ingests all content from DB/CMS
- Real-time updates: webhook triggers re-index of changed documents within 60 seconds
- Nightly full re-index: runs at 2am UTC as safety net for any missed webhooks

---

### 2. Search Widget Integration

Embedded in every client platform via a drop-in React component. The widget provides:

**Features**:
- **Instant search**: results appear as user types, starting at 2 characters
- **Typo tolerance**: "prduct" finds "product", "web disegn" finds "web design"
- **Filters**: by content type, date range, category, price range (e-com), in-stock only (e-com)
- **Facets**: shows count per filter category so users know what's available
- **Highlighting**: matched keywords highlighted in bold in results
- **Custom ranking**: per business type

**Ranking Rules Per Business Type**:

| Business Type | Ranking Boost | Ranking Demote |
|---|---|---|
| E-Commerce | In-stock products, recent products | Out-of-stock |
| SaaS | Feature docs, getting-started articles | Changelog entries |
| Website | Service pages, key landing pages | Old blog posts |
| dApp | Roadmap/FAQ (user intent focus) | None |

**Search Result Display**:
- Title (highlighted)
- URL breadcrumb
- Description snippet (highlighted, up to 160 chars)
- Content type badge (Page / Product / Blog / Doc)
- For products: price + in-stock indicator
- Keyboard navigation: ↑↓ arrows, Enter to open, Esc to close

---

### 3. Federated Search — Prolific Hub

A unified search interface that queries across ALL ProlificWebCraft client platforms simultaneously.

**Architecture**:
```
User Query: "web design NYC"
         │
         ▼
Prolific Hub Search API
  ├── Query Client A's Typesense instance
  ├── Query Client B's Typesense instance
  ├── Query Client C's Typesense instance
  └── ...Query N clients
         │
         ▼
Merge + Deduplicate results
Rank by relevance score + opt-in boost
         │
         ▼
Return: unified results page
  ├── [Client A] NYC Web Design Agency — clienta.com/services
  ├── [Client B] Web Design for NYC Restaurants — clientb.com/web-design
  └── [Client C] Affordable NYC Business Websites — clientc.com
```

**Opt-In Model**:
- Default: each client's search is isolated (their users only search their content)
- Optional "Cross-Platform Discovery" enrollment: client opts in, their content appears in Prolific Hub
- Benefit to client: inter-client referral traffic, wider discovery
- Benefit to ProlificWebCraft: network effect grows value of entire platform

**Prolific Hub URL**: `search.prolificwebcraft.com`

**Revenue Model**: Prolific Hub drives referral traffic between clients → clients see value → retainer churn reduces.

---

### 4. SEO Impact Tracking

Bridges the gap between what users search internally (on-site) and what they search externally (Google/Bing).

**Data Flow**:
```
On-site search query → Typesense analytics log
                              │
                              ▼
Monthly: map to Google Search Console
  "Users searched 'plumbing estimate' 34 times internally
   → GSC shows 0 impressions for 'plumbing estimate'
   → CONTENT GAP IDENTIFIED"
```

**Content Gap Report** (generated monthly, delivered to client):

```markdown
## Monthly Content Gap Report — [CLIENT_NAME]
### Period: [MONTH YEAR]

### Top Unmet Search Queries This Month
| Search Query | Internal Searches | Existing Page? | Recommended Action |
|---|---|---|---|
| plumbing estimate | 47 | No | Write "Free Plumbing Estimate" landing page |
| emergency plumber | 34 | No | Create /emergency-plumber service page |
| drain cleaning cost | 28 | No | Write blog: "How Much Does Drain Cleaning Cost?" |
| [keyword] | N | No/Yes | [action] |

### Zero-Result Queries (users found nothing)
- "water heater replacement" — 19 searches, 0 results
- "pipe inspection" — 14 searches, 0 results
- ACTION: Add these terms to existing service pages OR create new pages

### SEO → Search Alignment Score: 62/100
*Score improves as content gaps are filled*

### Recommended Content for Next Month (prioritized by search volume):
1. "Free Plumbing Estimate" page (47 potential internal + likely high external demand)
2. "Emergency Plumber [City]" page (34 internal + high local search intent)
3. Blog: "Drain Cleaning Cost Guide" (28 internal + informational SEO opportunity)
```

---

### 5. ROI Analytics Dashboard

Tracks search performance tied directly to business outcomes.

**Metrics Tracked Per Client**:

| Metric | Description | Frequency |
|---|---|---|
| Total searches | Search volume on client platform | Daily |
| Zero-result rate | % of searches returning no results | Daily |
| Top queries | Ranked list of most searched terms | Weekly |
| Search-to-click rate | % of searches that result in a click | Weekly |
| Search-to-conversion rate | % of searches that lead to a purchase/lead/signup | Monthly |
| Revenue attributed to search | Dollar value of conversions from search sessions | Monthly |
| Search index coverage | % of site content indexed vs. total pages | Weekly |
| Indexing freshness | Average age of indexed documents | Weekly |

**Monthly ROI Report Template**:

```markdown
## Search Engine ROI Report — [CLIENT_NAME]
### Period: [MONTH YEAR]

### Search Volume
- Total searches this month: 1,247
- Search volume growth vs. last month: +18%
- Top 5 queries: [list]

### Search Quality
- Zero-result rate: 8.3% (benchmark: <10% = good)
- Search-to-click rate: 61%
- Average results per query: 8.4

### Business Impact
- Search sessions that led to conversions: 143
- Estimated revenue from search: $4,290
- Search ROI (vs. $199/mo package cost): 21.5x

### Index Health
- Total documents indexed: 847
- Pages not indexed: 3 (see below)
- Last full sync: [date/time]
- Average sync latency: 22 seconds

### Alerts
- ⚠️  "wholesale pricing" searched 31 times, zero results — content gap
- ⚠️  3 product pages not indexed — check webhook logs

### Recommended Actions
1. Create a "Wholesale Pricing" page (high search intent, zero results)
2. Fix webhook for 3 un-indexed product pages
3. Add "in-stock" filter to search widget (57% of searches appear price-related)
```

---

### 6. Search Engine Submission Automation

Automatically notifies Google, Bing, Yandex, and DuckDuckGo when new or updated content is published.

**Triggers**:
- New page published → submit URL immediately
- Page updated → submit URL immediately
- Nightly batch: re-submit any URLs not confirmed indexed within 7 days

**Monitoring**:
- Polls Google Search Console API daily for indexation status of all submitted URLs
- Flags pages that drop out of index (were indexed, now returning "Not indexed")
- Auto-resubmits stale pages (indexed >90 days ago with no recent change)
- Alerts via email/Slack when: index drops >5% in a week, any page 404s, coverage errors increase

---

## Critical Rules

1. **API key split mandatory.** Typesense generates two keys at deploy time:
   - `SEARCH_ONLY_KEY` — read-only, embedded in frontend code, safe to expose
   - `ADMIN_KEY` — full read/write, stored only in server environment variables, never in frontend code
   
2. **Index new content within 60 seconds of publish.** Webhook handlers must be idempotent and include retry logic (max 3 retries with exponential backoff). If a webhook fails, a dead-letter queue holds the document for nightly re-sync.

3. **Zero-result alert threshold.** If any single query term generates zero results 10 or more times within a 7-day rolling window, an alert fires to the client and to the SEO Growth Agent for content gap action.

4. **Never index private content.** Content behind authentication walls (user dashboards, private messages, payment details, admin panels) is never added to any Typesense collection. Index only content accessible to unauthenticated users, or content the user who searched it has permission to see (for authenticated search within SaaS apps).

---

## Key Deliverables

### Deliverable 1 — Docker Compose for Typesense Cluster

```yaml
# docker-compose.yml — Prolific Search Engine (Typesense)
version: "3.8"

services:
  typesense-node-1:
    image: typesense/typesense:0.25.2
    container_name: prolific-search-node-1
    restart: unless-stopped
    ports:
      - "8108:8108"
    volumes:
      - typesense_data_1:/data
    command: >
      --data-dir /data
      --api-key ${TYPESENSE_ADMIN_API_KEY}
      --listen-port 8108
      --enable-cors
      --cors-domains ${ALLOWED_ORIGINS}
      --log-slow-requests-time-ms 200
    environment:
      - TYPESENSE_ADMIN_API_KEY=${TYPESENSE_ADMIN_API_KEY}
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8108/health"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 10s
    networks:
      - prolific-search-net

  typesense-node-2:
    image: typesense/typesense:0.25.2
    container_name: prolific-search-node-2
    restart: unless-stopped
    ports:
      - "8109:8108"
    volumes:
      - typesense_data_2:/data
    command: >
      --data-dir /data
      --api-key ${TYPESENSE_ADMIN_API_KEY}
      --listen-port 8108
      --enable-cors
      --cors-domains ${ALLOWED_ORIGINS}
    environment:
      - TYPESENSE_ADMIN_API_KEY=${TYPESENSE_ADMIN_API_KEY}
    networks:
      - prolific-search-net

  nginx-lb:
    image: nginx:alpine
    container_name: prolific-search-lb
    restart: unless-stopped
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./nginx/ssl:/etc/nginx/ssl:ro
    depends_on:
      - typesense-node-1
      - typesense-node-2
    networks:
      - prolific-search-net

  sync-worker:
    build: ./sync-worker
    container_name: prolific-search-sync
    restart: unless-stopped
    environment:
      - TYPESENSE_HOST=typesense-node-1
      - TYPESENSE_PORT=8108
      - TYPESENSE_ADMIN_API_KEY=${TYPESENSE_ADMIN_API_KEY}
      - DATABASE_URL=${DATABASE_URL}
      - WEBHOOK_SECRET=${WEBHOOK_SECRET}
    ports:
      - "3001:3001"
    depends_on:
      typesense-node-1:
        condition: service_healthy
    networks:
      - prolific-search-net

volumes:
  typesense_data_1:
    driver: local
  typesense_data_2:
    driver: local

networks:
  prolific-search-net:
    driver: bridge
```

---

### Deliverable 2 — Typesense Collection Schemas

```typescript
// lib/typesense-schemas.ts
import Typesense from 'typesense';

const client = new Typesense.Client({
  nodes: [{ host: process.env.TYPESENSE_HOST!, port: 8108, protocol: 'http' }],
  apiKey: process.env.TYPESENSE_ADMIN_API_KEY!,
  connectionTimeoutSeconds: 2,
});

export const COLLECTION_SCHEMAS = {
  pages: {
    name: 'pages',
    fields: [
      { name: 'id', type: 'string' },
      { name: 'title', type: 'string', facet: false },
      { name: 'slug', type: 'string', index: false },
      { name: 'url', type: 'string', index: false },
      { name: 'description', type: 'string', optional: true },
      { name: 'content', type: 'string', optional: true },
      { name: 'page_type', type: 'string', facet: true },
      { name: 'updated_at', type: 'int64' },
      { name: 'site_id', type: 'string', facet: true },
    ],
    default_sorting_field: 'updated_at',
  },

  products: {
    name: 'products',
    fields: [
      { name: 'id', type: 'string' },
      { name: 'name', type: 'string', facet: false },
      { name: 'sku', type: 'string', optional: true },
      { name: 'description', type: 'string', optional: true },
      { name: 'price', type: 'float', facet: false },
      { name: 'compare_at_price', type: 'float', optional: true, facet: false },
      { name: 'category', type: 'string', facet: true },
      { name: 'tags', type: 'string[]', facet: true },
      { name: 'in_stock', type: 'bool', facet: true },
      { name: 'inventory_count', type: 'int32', optional: true },
      { name: 'image_url', type: 'string', optional: true, index: false },
      { name: 'url', type: 'string', index: false },
      { name: 'site_id', type: 'string', facet: true },
      { name: 'updated_at', type: 'int64' },
    ],
    default_sorting_field: 'updated_at',
  },

  posts: {
    name: 'posts',
    fields: [
      { name: 'id', type: 'string' },
      { name: 'title', type: 'string' },
      { name: 'slug', type: 'string', index: false },
      { name: 'excerpt', type: 'string', optional: true },
      { name: 'body', type: 'string', optional: true },
      { name: 'author', type: 'string', facet: true, optional: true },
      { name: 'tags', type: 'string[]', facet: true, optional: true },
      { name: 'url', type: 'string', index: false },
      { name: 'published_at', type: 'int64' },
      { name: 'site_id', type: 'string', facet: true },
    ],
    default_sorting_field: 'published_at',
  },

  saas_docs: {
    name: 'saas_docs',
    fields: [
      { name: 'id', type: 'string' },
      { name: 'title', type: 'string' },
      { name: 'section', type: 'string', facet: true },
      { name: 'content', type: 'string' },
      { name: 'feature_area', type: 'string', facet: true, optional: true },
      { name: 'url', type: 'string', index: false },
      { name: 'updated_at', type: 'int64' },
      { name: 'site_id', type: 'string', facet: true },
    ],
    default_sorting_field: 'updated_at',
  },
} as const;

export async function initializeCollections() {
  for (const schema of Object.values(COLLECTION_SCHEMAS)) {
    try {
      await client.collections(schema.name).retrieve();
      console.log(`Collection '${schema.name}' already exists — skipping.`);
    } catch {
      await client.collections().create(schema as any);
      console.log(`Created collection '${schema.name}'.`);
    }
  }
}
```

---

### Deliverable 3 — Node.js Webhook Handler for Content Sync

```typescript
// sync-worker/webhook-handler.ts
import express, { Request, Response } from 'express';
import crypto from 'crypto';
import Typesense from 'typesense';

const app = express();
app.use(express.json({ limit: '10mb' }));

const typesense = new Typesense.Client({
  nodes: [{ host: process.env.TYPESENSE_HOST!, port: 8108, protocol: 'http' }],
  apiKey: process.env.TYPESENSE_ADMIN_API_KEY!,
  connectionTimeoutSeconds: 5,
});

// Verify webhook signature (HMAC-SHA256)
function verifyWebhookSignature(payload: string, signature: string, secret: string): boolean {
  const expected = crypto.createHmac('sha256', secret).update(payload).digest('hex');
  return crypto.timingSafeEqual(Buffer.from(signature, 'hex'), Buffer.from(expected, 'hex'));
}

// Retry wrapper with exponential backoff
async function withRetry<T>(fn: () => Promise<T>, maxRetries = 3): Promise<T> {
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      return await fn();
    } catch (err) {
      if (attempt === maxRetries) throw err;
      await new Promise(resolve => setTimeout(resolve, 1000 * Math.pow(2, attempt)));
    }
  }
  throw new Error('Unreachable');
}

// POST /webhooks/content-changed
app.post('/webhooks/content-changed', async (req: Request, res: Response) => {
  const signature = req.headers['x-prolific-signature'] as string;
  const rawBody = JSON.stringify(req.body);

  if (!verifyWebhookSignature(rawBody, signature, process.env.WEBHOOK_SECRET!)) {
    return res.status(401).json({ error: 'Invalid signature' });
  }

  const { event, collection, document, site_id } = req.body as {
    event: 'created' | 'updated' | 'deleted';
    collection: 'pages' | 'products' | 'posts' | 'saas_docs' | 'dapp_pages';
    document: Record<string, any>;
    site_id: string;
  };

  // Validate collection name
  const validCollections = ['pages', 'products', 'posts', 'saas_docs', 'dapp_pages'];
  if (!validCollections.includes(collection)) {
    return res.status(400).json({ error: 'Unknown collection' });
  }

  // Respond immediately — process async
  res.json({ received: true, queued: true });

  try {
    if (event === 'deleted') {
      await withRetry(() =>
        typesense.collections(collection).documents(document.id).delete()
      );
      console.log(`[SEARCH] Deleted ${collection}/${document.id} from ${site_id}`);
    } else {
      // Upsert (create or update)
      const doc = {
        ...document,
        site_id,
        updated_at: Math.floor(Date.now() / 1000),
      };
      await withRetry(() =>
        typesense.collections(collection).documents().upsert(doc)
      );
      console.log(`[SEARCH] Upserted ${collection}/${document.id} for ${site_id} (event: ${event})`);
    }
  } catch (err) {
    console.error(`[SEARCH] Failed to sync ${collection}/${document.id}:`, err);
    // In production: push to dead-letter queue for nightly re-sync
  }
});

// POST /webhooks/page-published — triggers search engine submission
app.post('/webhooks/page-published', async (req: Request, res: Response) => {
  const { url, site_id } = req.body;
  res.json({ received: true });

  // Submit to Google Indexing API
  try {
    await submitUrlToGoogle(url);
    await submitUrlToBing(url);
    console.log(`[SEO] Submitted ${url} to Google + Bing`);
  } catch (err) {
    console.error(`[SEO] Submission failed for ${url}:`, err);
  }
});

async function submitUrlToGoogle(url: string) {
  const { google } = await import('googleapis');
  const auth = new google.auth.GoogleAuth({
    keyFile: process.env.GOOGLE_SERVICE_ACCOUNT_KEY_FILE,
    scopes: ['https://www.googleapis.com/auth/indexing'],
  });
  const indexing = google.indexing({ version: 'v3', auth });
  await indexing.urlNotifications.publish({
    requestBody: { url, type: 'URL_UPDATED' },
  });
}

async function submitUrlToBing(url: string) {
  await fetch(`https://ssl.bing.com/webmaster/api.svc/json/SubmitUrl?apikey=${process.env.BING_API_KEY}`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ siteUrl: process.env.SITE_URL, url }),
  });
}

// GET /health
app.get('/health', (_req, res) => res.json({ status: 'ok', timestamp: new Date().toISOString() }));

const PORT = process.env.PORT || 3001;
app.listen(PORT, () => console.log(`[SEARCH] Sync worker running on port ${PORT}`));
```

---

### Deliverable 4 — React Search Widget Component

```tsx
// components/search/ProlificSearchWidget.tsx
import React, { useState, useEffect, useRef, useCallback } from 'react';
import Typesense from 'typesense';

interface SearchResult {
  id: string;
  title: string;
  url: string;
  description?: string;
  price?: number;
  in_stock?: boolean;
  page_type?: string;
  _highlight?: {
    title?: { snippet: string };
    description?: { snippet: string };
  };
}

interface SearchWidgetProps {
  typesenseHost: string;
  searchApiKey: string;
  collections?: string[];
  placeholder?: string;
  maxResults?: number;
  onResultClick?: (result: SearchResult) => void;
}

export default function ProlificSearchWidget({
  typesenseHost,
  searchApiKey,
  collections = ['pages', 'posts', 'products'],
  placeholder = 'Search...',
  maxResults = 8,
  onResultClick,
}: SearchWidgetProps) {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState<SearchResult[]>([]);
  const [loading, setLoading] = useState(false);
  const [open, setOpen] = useState(false);
  const [selected, setSelected] = useState(-1);
  const inputRef = useRef<HTMLInputElement>(null);
  const debounceRef = useRef<ReturnType<typeof setTimeout>>();

  const client = useRef(
    new Typesense.Client({
      nodes: [{ host: typesenseHost, port: 443, protocol: 'https' }],
      apiKey: searchApiKey,
      connectionTimeoutSeconds: 2,
    })
  );

  const search = useCallback(async (q: string) => {
    if (q.length < 2) { setResults([]); return; }
    setLoading(true);
    try {
      const searchRequests = collections.map(c => ({
        collection: c,
        q,
        query_by: c === 'products' ? 'name,description,tags' : 'title,description,content',
        highlight_full_fields: 'title,description',
        per_page: Math.ceil(maxResults / collections.length),
        sort_by: c === 'products' ? 'in_stock:desc,_text_match:desc' : '_text_match:desc',
      }));

      const response = await client.current.multiSearch.perform({ searches: searchRequests as any }, {});
      const merged: SearchResult[] = [];

      response.results.forEach((r: any) => {
        r.hits?.forEach((hit: any) => {
          merged.push({
            ...hit.document,
            _highlight: hit.highlight,
          });
        });
      });

      setResults(merged.slice(0, maxResults));
      setOpen(true);
    } catch (err) {
      console.error('Search error:', err);
    } finally {
      setLoading(false);
    }
  }, [collections, maxResults]);

  useEffect(() => {
    clearTimeout(debounceRef.current);
    if (!query) { setResults([]); setOpen(false); return; }
    debounceRef.current = setTimeout(() => search(query), 200);
    return () => clearTimeout(debounceRef.current);
  }, [query, search]);

  const handleKeyDown = (e: React.KeyboardEvent) => {
    if (e.key === 'ArrowDown') setSelected(s => Math.min(s + 1, results.length - 1));
    else if (e.key === 'ArrowUp') setSelected(s => Math.max(s - 1, 0));
    else if (e.key === 'Enter' && selected >= 0) {
      const r = results[selected];
      onResultClick?.(r);
      window.location.href = r.url;
    } else if (e.key === 'Escape') {
      setOpen(false);
      setQuery('');
    }
  };

  const highlightText = (result: SearchResult, field: 'title' | 'description') => {
    const snippet = result._highlight?.[field]?.snippet;
    if (!snippet) return field === 'title' ? result.title : result.description ?? '';
    return snippet.replace(/<mark>/g, '<strong>').replace(/<\/mark>/g, '</strong>');
  };

  const getBadgeColor = (type?: string) => {
    const map: Record<string, string> = {
      product: '#10B981',
      post: '#3B82F6',
      page: '#8B5CF6',
      docs: '#F59E0B',
    };
    return map[type ?? 'page'] ?? '#6B7280';
  };

  return (
    <div style={{ position: 'relative', width: '100%', maxWidth: 560, fontFamily: 'Inter, sans-serif' }}>
      <div style={{ position: 'relative' }}>
        <span style={{ position: 'absolute', left: 12, top: '50%', transform: 'translateY(-50%)', color: '#9CA3AF', fontSize: 16 }}>
          🔭
        </span>
        <input
          ref={inputRef}
          type="search"
          value={query}
          onChange={e => { setQuery(e.target.value); setSelected(-1); }}
          onKeyDown={handleKeyDown}
          onFocus={() => results.length > 0 && setOpen(true)}
          placeholder={placeholder}
          autoComplete="off"
          style={{
            width: '100%',
            padding: '0.625rem 1rem 0.625rem 2.5rem',
            border: '1.5px solid #D1D5DB',
            borderRadius: 10,
            fontSize: '0.9375rem',
            outline: 'none',
            boxSizing: 'border-box',
            background: 'white',
            transition: 'border-color 0.15s',
          }}
          onMouseOver={e => ((e.target as HTMLInputElement).style.borderColor = '#F59E0B')}
          onMouseOut={e => ((e.target as HTMLInputElement).style.borderColor = '#D1D5DB')}
        />
        {loading && (
          <span style={{ position: 'absolute', right: 12, top: '50%', transform: 'translateY(-50%)', color: '#9CA3AF', fontSize: 12 }}>
            ···
          </span>
        )}
      </div>

      {open && results.length > 0 && (
        <div
          style={{
            position: 'absolute',
            top: '100%',
            left: 0,
            right: 0,
            marginTop: 4,
            background: 'white',
            border: '1px solid #E5E7EB',
            borderRadius: 10,
            boxShadow: '0 10px 40px rgba(0,0,0,0.12)',
            zIndex: 9999,
            overflow: 'hidden',
          }}
        >
          {results.map((result, i) => (
            <a
              key={result.id}
              href={result.url}
              onClick={() => onResultClick?.(result)}
              style={{
                display: 'flex',
                alignItems: 'flex-start',
                gap: '0.75rem',
                padding: '0.75rem 1rem',
                textDecoration: 'none',
                background: selected === i ? '#FEF3C7' : 'white',
                borderBottom: i < results.length - 1 ? '1px solid #F3F4F6' : 'none',
                transition: 'background 0.1s',
              }}
              onMouseEnter={() => setSelected(i)}
            >
              <div style={{ flex: 1, minWidth: 0 }}>
                <div style={{ display: 'flex', alignItems: 'center', gap: '0.5rem', marginBottom: '0.125rem' }}>
                  <span
                    dangerouslySetInnerHTML={{ __html: highlightText(result, 'title') }}
                    style={{ fontWeight: 500, fontSize: '0.9375rem', color: '#111827', whiteSpace: 'nowrap', overflow: 'hidden', textOverflow: 'ellipsis' }}
                  />
                  <span style={{
                    fontSize: '0.6875rem', fontWeight: 600, padding: '0.125rem 0.375rem',
                    borderRadius: 4, background: getBadgeColor(result.page_type) + '22',
                    color: getBadgeColor(result.page_type), flexShrink: 0,
                  }}>
                    {result.page_type?.toUpperCase() ?? 'PAGE'}
                  </span>
                  {result.price !== undefined && (
                    <span style={{ fontSize: '0.875rem', fontWeight: 600, color: '#10B981', flexShrink: 0 }}>
                      ${result.price.toFixed(2)}
                    </span>
                  )}
                </div>
                {result.description && (
                  <span
                    dangerouslySetInnerHTML={{ __html: highlightText(result, 'description') }}
                    style={{ fontSize: '0.8125rem', color: '#6B7280', display: 'block', overflow: 'hidden', textOverflow: 'ellipsis', whiteSpace: 'nowrap' }}
                  />
                )}
                <span style={{ fontSize: '0.75rem', color: '#9CA3AF' }}>{result.url}</span>
              </div>
            </a>
          ))}

          <div style={{ padding: '0.5rem 1rem', background: '#F9FAFB', fontSize: '0.75rem', color: '#9CA3AF', textAlign: 'right' }}>
            Powered by Prolific Search Engine
          </div>
        </div>
      )}

      {open && query.length >= 2 && results.length === 0 && !loading && (
        <div style={{
          position: 'absolute', top: '100%', left: 0, right: 0, marginTop: 4,
          background: 'white', border: '1px solid #E5E7EB', borderRadius: 10,
          padding: '1rem', textAlign: 'center', color: '#6B7280', fontSize: '0.875rem',
          boxShadow: '0 10px 40px rgba(0,0,0,0.12)', zIndex: 9999,
        }}>
          No results for "<strong>{query}</strong>". Try a different term.
        </div>
      )}
    </div>
  );
}
```

---

### Deliverable 5 — Search Engine Submission Automation Script

```javascript
// scripts/search-engine-submit.js
// Node.js script — submits all site URLs to Google, Bing, Yandex
// Run: node scripts/search-engine-submit.js --site-url https://client.com

const { google } = require('googleapis');
const fetch = require('node-fetch');
const { parseStringPromise } = require('xml2js');
require('dotenv').config();

const args = process.argv.slice(2);
const siteUrlArg = args.find(a => a.startsWith('--site-url='));
const SITE_URL = siteUrlArg ? siteUrlArg.split('=')[1] : process.env.SITE_URL;

async function fetchSitemapUrls(sitemapUrl) {
  const res = await fetch(sitemapUrl);
  if (!res.ok) throw new Error(`Failed to fetch sitemap: ${res.status}`);
  const xml = await res.text();
  const parsed = await parseStringPromise(xml);
  const urls = parsed.urlset?.url?.map(u => u.loc[0]) ?? [];
  console.log(`[SITEMAP] Found ${urls.length} URLs`);
  return urls;
}

async function submitToGoogle(urls) {
  const auth = new google.auth.GoogleAuth({
    keyFile: process.env.GOOGLE_SERVICE_ACCOUNT_KEY_FILE,
    scopes: ['https://www.googleapis.com/auth/indexing'],
  });
  const indexing = google.indexing({ version: 'v3', auth });

  let success = 0, failed = 0;
  for (const url of urls) {
    try {
      await indexing.urlNotifications.publish({
        requestBody: { url, type: 'URL_UPDATED' },
      });
      success++;
    } catch (err) {
      console.warn(`[GOOGLE] Failed: ${url} — ${err.message}`);
      failed++;
    }
    // Rate limit: 200 URLs/day per property — add delay if needed
    await new Promise(r => setTimeout(r, 100));
  }
  console.log(`[GOOGLE] Submitted: ${success} success, ${failed} failed`);
}

async function submitToBing(urls) {
  if (!process.env.BING_API_KEY) { console.log('[BING] No API key — skipping'); return; }

  const res = await fetch(
    `https://ssl.bing.com/webmaster/api.svc/json/SubmitUrlbatch?apikey=${process.env.BING_API_KEY}`,
    {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ siteUrl: SITE_URL, urlList: urls.slice(0, 500) }),
    }
  );
  const data = await res.json();
  console.log(`[BING] Response:`, data.d ?? data);
}

async function submitToYandex(urls) {
  if (!process.env.YANDEX_API_KEY) { console.log('[YANDEX] No API key — skipping'); return; }

  const res = await fetch(
    `https://opi.yandex.ru/indexer/v1/reindex?host=${encodeURIComponent(SITE_URL)}&data=${encodeURIComponent(urls.join('\n'))}`,
    {
      method: 'POST',
      headers: {
        'Authorization': `OAuth ${process.env.YANDEX_API_KEY}`,
        'Content-Type': 'text/plain',
      },
    }
  );
  console.log(`[YANDEX] Status: ${res.status}`);
}

async function main() {
  if (!SITE_URL) {
    console.error('ERROR: SITE_URL required. Use --site-url=https://... or set SITE_URL env var.');
    process.exit(1);
  }

  console.log(`[SUBMIT] Starting submission for: ${SITE_URL}`);
  const sitemapUrl = `${SITE_URL.replace(/\/$/, '')}/sitemap.xml`;

  let urls;
  try {
    urls = await fetchSitemapUrls(sitemapUrl);
  } catch (err) {
    console.error('[SITEMAP] Failed to fetch sitemap:', err.message);
    process.exit(1);
  }

  await Promise.allSettled([
    submitToGoogle(urls),
    submitToBing(urls),
    submitToYandex(urls),
  ]);

  console.log('[SUBMIT] All engines notified. Monitor indexation in respective webmaster tools.');
}

main().catch(err => {
  console.error('Fatal error:', err);
  process.exit(1);
});
```

---

*Prolific Search Engine Agent — ProlificWebCraft Internal Specification v1.0.0*
