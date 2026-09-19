import requests

API_URL = "https://api.opensea.io/api/v2/collections"

API_KEY = "YOUR_OPENSEA_API_KEY"
COLLECTION_SLUG = "doodles"

HEADERS = {
    "accept": "application/json",
    "x-api-key": API_KEY
}


def get_collection(slug):
    url = f"{API_URL}/{slug}"

    response = requests.get(
        url,
        headers=HEADERS,
        timeout=15
    )

    response.raise_for_status()

    return response.json()


def display_collection(data):
    print("NFT Collection Tracker")
    print("-" * 40)

    print(f"Name:        {data.get('name', 'N/A')}")
    print(f"Slug:        {data.get('collection', 'N/A')}")
    print(f"Description: {data.get('description', 'N/A')[:100]}")

    print(f"Image:       {data.get('image_url', 'N/A')}")
    print(f"Twitter:     {data.get('twitter_username', 'N/A')}")
    print(f"Discord:     {data.get('discord_url', 'N/A')}")


():
    if API_KEY == "YOUR_OPENSEA_API_KEY":
        raise ValueError(
            "Please add your OpenSea API key."
        )

    try:
        collection = get_collection(
            COLLECTION_SLUG
        )

        display_collection(collection)

    except requests.RequestException as error:
        print(f"API Error: {error}")


if name == "main":
    main()
