<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Category</th>
        <th scope="col">Name</th>
        <th scope="col" width="300">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="restaurant in restaurants" :key="restaurant.id">
        <th scope="row">
          {{ restaurant.id }}
        </th>
        <td>{{ restaurant.Category ? restaurant.Category.name : "未分類" }}</td>
        <td>{{ restaurant.name }}</td>
        <td class="d-flex justify-content-between">
          <router-link 
            :to="{ name: 'admin-restaurant', params: { id: restaurant.id}}" 
            class="btn btn-link"
          >Show</router-link>

          <router-link
            :to="{ name: 'admin-restaurant-edit', params: { id: restaurant.id }}"
            class="btn btn-link"
          >Edit
          </router-link>

          <button 
            type="button" 
            class="btn btn-link"
            @click.prevent.stop="deleteRestaurant(restaurant.id)"
          >Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Malinda Ward",
      tel: "068-332-5988 x7248",
      address: "319 Morissette Wells",
      opening_hours: "08:00",
      description: "Iure facere corporis laboriosam veritatis.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=34.26217016006026",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 2,
      name: "Josianne Morissette",
      tel: "186-348-1096 x7161",
      address: "98892 Nat Center",
      opening_hours: "08:00",
      description: "quisquam",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=7.247830906750674",
      viewCounts: 1,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-02-01T14:47:22.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 3,
      name: "Jose Walker",
      tel: "(029) 558-5288",
      address: "8632 Crona Pass",
      opening_hours: "08:00",
      description:
        "Ut consequatur est totam sit laudantium.\nQuod corrupti neque a corporis saepe.\nUt velit odit ea omnis aut minima.\nNeque quos dolor ut omnis.\nQuidem deleniti corrupti dolorum dicta est quisquam beatae aut consequatur.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=29.312683373700963",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 4,
      name: "Patricia Little Sr.",
      tel: "643.853.7837 x9477",
      address: "76073 Streich Rapids",
      opening_hours: "08:00",
      description:
        "Voluptatibus modi aut et sit non.\nIusto facere nihil et quia quisquam aut error quasi ratione.\nSoluta velit voluptatum incidunt iste placeat quia.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=85.21044778500082",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 5,
      name: "Leone Williamson",
      tel: "669.305.8376 x8000",
      address: "445 Ines Falls",
      opening_hours: "08:00",
      description:
        "Aut autem veniam. Est vel molestiae ex nihil voluptates qui exercitationem enim adipisci.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=64.96885668402521",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 6,
      name: "Jazmyn Dickens",
      tel: "267-121-4754 x505",
      address: "646 Lonnie Rapids",
      opening_hours: "08:00",
      description:
        "Voluptatem vero voluptate. Nostrum nam pariatur. Molestiae nisi expedita reprehenderit dignissimos nostrum qui iusto voluptas. Omnis ea sit consectetur necessitatibus architecto odio eaque. Vel dolore nam accusamus et eligendi cumque tempora.\n \rIure voluptatibus ipsa rerum voluptate repellendus aut. Quam voluptas quidem animi amet dolores ipsum alias sapiente omnis. Et expedita atque dignissimos atque.\n \rNulla ut saepe suscipit qui ipsa provident. Quas nobis perferendis sequi. Ipsa officia repudiandae non minima perspiciatis aut. Non molestiae harum consequatur sed reprehenderit quo.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=87.96655784096656",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 7,
      name: "Oran Balistreri MD",
      tel: "(147) 366-5481",
      address: "429 Anderson Stravenue",
      opening_hours: "08:00",
      description: "sapiente quos reprehenderit",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=91.1211519149812",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 8,
      name: "Filomena Luettgen",
      tel: "755-247-1462",
      address: "00639 Kirlin Lake",
      opening_hours: "08:00",
      description:
        "Aut vel sit expedita assumenda beatae voluptas at.\nTenetur et et eos repudiandae omnis.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=86.13151766110238",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 9,
      name: "Norris Walter",
      tel: "618-464-8689",
      address: "876 Hegmann Mews",
      opening_hours: "08:00",
      description:
        "Cumque repellat sit eum ratione rerum animi maxime consequatur dolorem. Vel quia consectetur sunt et. Id quo enim reprehenderit eveniet unde impedit est explicabo.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=59.627307029976606",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 10,
      name: "Marcus Zulauf",
      tel: "1-443-671-4596",
      address: "13859 Waters Ville",
      opening_hours: "08:00",
      description: "Blanditiis repellat aperiam.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=99.83482401774549",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 11,
      name: "Carleton Kirlin",
      tel: "017.812.2853 x1202",
      address: "4142 Florian Way",
      opening_hours: "08:00",
      description: "Autem omnis autem deleniti et voluptas laborum.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=11.700904416944047",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 12,
      name: "Scarlett Douglas",
      tel: "364-916-2069",
      address: "79668 Augusta Plains",
      opening_hours: "08:00",
      description:
        "Quos a sapiente.\nQuod nam repellat aut ea facere reprehenderit in atque unde.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=31.70367555368314",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 13,
      name: "Miss Annetta Schuster",
      tel: "1-000-529-6204 x97986",
      address: "484 Bauch Circle",
      opening_hours: "08:00",
      description: "repellendus ipsum qui",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=77.77771864610396",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 14,
      name: "Rey Rice",
      tel: "(812) 555-5918",
      address: "296 Kianna Harbor",
      opening_hours: "08:00",
      description:
        "Eligendi explicabo repellendus laboriosam officia eligendi.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=71.61502498394181",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 15,
      name: "Mr. June Nienow",
      tel: "1-987-074-8129 x95584",
      address: "3284 Turner Knolls",
      opening_hours: "08:00",
      description: "temporibus qui facilis",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=0.1765011151409368",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 16,
      name: "Derrick Runolfsdottir",
      tel: "294.429.1038 x897",
      address: "1160 Leland Roads",
      opening_hours: "08:00",
      description:
        "Ut enim cum qui velit. Cumque occaecati quia. Dolores voluptatem eius quaerat laudantium. Explicabo distinctio laborum natus quaerat iste aut.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=6.307083612267572",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 17,
      name: "Duncan Kassulke",
      tel: "(944) 079-9598",
      address: "59633 Prohaska River",
      opening_hours: "08:00",
      description: "atque",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=35.99103410903175",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 18,
      name: "Jaycee Gleichner",
      tel: "764-002-9597 x1305",
      address: "2922 Sven Springs",
      opening_hours: "08:00",
      description:
        "Sed voluptas voluptatem enim est. Nemo aut commodi. Aut suscipit qui non quis cum autem id voluptas. Porro dolores illo harum aut dolores ut aut et.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=72.68941221002791",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 19,
      name: "Francisca Kohler",
      tel: "(740) 553-2109",
      address: "915 Cormier Walks",
      opening_hours: "08:00",
      description: "Soluta quos voluptatem qui.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=7.906401984053835",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 20,
      name: "Asa Ortiz",
      tel: "724.501.1498 x3419",
      address: "70918 Hoeger Cape",
      opening_hours: "08:00",
      description:
        "Recusandae distinctio nostrum deserunt ea voluptatem totam similique. Dicta praesentium sit minus. Vel laborum est. Est voluptate eligendi ut et dolorem est.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=28.213601656299268",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 21,
      name: "Hannah Braun",
      tel: "139-183-5874 x61802",
      address: "5348 Jany Isle",
      opening_hours: "08:00",
      description:
        "Eum incidunt unde ab fugit. Veritatis soluta facilis eaque consequatur praesentium sint laborum dolorem. Dolorum est maxime architecto rem modi aut modi. Ut ea aut suscipit velit quibusdam.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=6.951693448012342",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 22,
      name: "Mr. Clarissa Nienow",
      tel: "167.978.4508 x00804",
      address: "152 Kennith Glens",
      opening_hours: "08:00",
      description: "a placeat neque",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=69.53410345977895",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 23,
      name: "Damon Nicolas",
      tel: "(819) 464-9257 x3067",
      address: "9667 Madison Underpass",
      opening_hours: "08:00",
      description:
        "Itaque harum dolores doloremque consequatur aliquid placeat occaecati dolor totam. Veniam harum quas vel hic rerum dignissimos officiis temporibus facere. Voluptatum sit aut.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=40.027755954732136",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 24,
      name: "Mertie Wunsch",
      tel: "737.019.8466 x34285",
      address: "39119 Wilson Orchard",
      opening_hours: "08:00",
      description:
        "Ut quo animi voluptate qui. Qui molestiae beatae dolore sequi dolorem cupiditate.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=34.56423405565807",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 25,
      name: "Braeden Pfeffer",
      tel: "364.600.8103 x576",
      address: "051 Hansen Shores",
      opening_hours: "08:00",
      description:
        "Officia molestiae id molestiae quaerat maxime sint enim ipsa rerum. Consequatur non cupiditate fuga a sapiente. Sit unde explicabo ex adipisci omnis.\n \rQuo cumque minima deleniti ut alias. Deleniti eligendi sint totam. Omnis voluptate asperiores ducimus ipsum non at et. Et sed quibusdam consequatur dolor voluptas.\n \rDolorem laudantium et quam in. Voluptas consequatur optio. Iste necessitatibus nulla.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=58.749423656025535",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 26,
      name: "Annabelle Rempel IV",
      tel: "867.250.3137 x2906",
      address: "185 Bernhard Circle",
      opening_hours: "08:00",
      description:
        "Cumque placeat assumenda repellat quo qui aut. Dignissimos illum repellat qui consequuntur. Qui quibusdam et eius debitis velit qui molestiae neque ut. Earum quod odit omnis aut quod dolorem rerum sint.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=77.07397309083373",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 27,
      name: "Christelle Wolf",
      tel: "461.267.4209",
      address: "26408 Bill Lodge",
      opening_hours: "08:00",
      description:
        "Quia quia fugit culpa vel ipsa magnam. Possimus ut cupiditate distinctio repellendus doloremque dignissimos itaque magnam delectus. Sint pariatur sit ut enim quis mollitia enim quam sit. Alias totam blanditiis est debitis aut quia veniam. Dolorem ab ea accusamus officia odit.\n \rPossimus et unde soluta. Eius amet animi iste cumque blanditiis enim adipisci. Fugiat consequatur expedita sit. Perferendis sapiente aperiam.\n \rTempora quod at asperiores dolore voluptatem sit. Laboriosam maiores voluptas veritatis optio cumque quae minima. Recusandae natus dolorem voluptatem magni.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=37.25599092174288",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 28,
      name: "Amina Block",
      tel: "604-883-5838 x932",
      address: "3532 Johann Springs",
      opening_hours: "08:00",
      description:
        "Nam et doloremque incidunt odio recusandae quis cumque. Sed ut suscipit nam maiores voluptatum aspernatur. Illum aut enim sint. Eveniet ipsum veniam facilis voluptatibus. Ex ad maiores. Eligendi omnis necessitatibus.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=50.92230681814487",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 29,
      name: "Johnpaul Heaney I",
      tel: "658.189.7780",
      address: "41024 Altenwerth Park",
      opening_hours: "08:00",
      description: "quam",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=43.90943641013658",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 30,
      name: "Cathrine Goodwin",
      tel: "676-023-2590 x394",
      address: "6050 Marvin Vista",
      opening_hours: "08:00",
      description: "Qui et saepe nostrum iusto dolores porro molestiae.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=20.745987993063018",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 31,
      name: "Nathen Miller",
      tel: "903.834.3794 x9140",
      address: "22952 Camron Forest",
      opening_hours: "08:00",
      description: "Id exercitationem nulla numquam non repellat voluptate.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=23.40910025101204",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 32,
      name: "Ron McGlynn",
      tel: "647-528-3603 x437",
      address: "118 Paucek Heights",
      opening_hours: "08:00",
      description: "perferendis",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=16.928390427429328",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 33,
      name: "Keyon Corkery",
      tel: "(422) 541-5129 x832",
      address: "74234 Ricardo Burgs",
      opening_hours: "08:00",
      description: "nihil inventore doloremque",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=33.757708877651524",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 34,
      name: "Mr. Modesta Klocko",
      tel: "244.645.9663 x53485",
      address: "0924 Emie Ford",
      opening_hours: "08:00",
      description:
        "Sed perferendis magnam eaque ullam cupiditate quisquam.\nDolor et ab et ducimus iste tempore.\nVoluptatum enim assumenda nemo ipsam quod.\nSint culpa velit.\nError temporibus quia est.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=93.47355337688856",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 35,
      name: "Grover Hilpert",
      tel: "000.322.4346",
      address: "19061 Douglas Stream",
      opening_hours: "08:00",
      description:
        "Blanditiis voluptatibus natus nostrum ipsum repellendus neque.\nVelit pariatur placeat dolorem ratione nostrum reprehenderit neque.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=95.53414277907973",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 36,
      name: "Maudie Johns",
      tel: "123-389-0295",
      address: "3750 Else Isle",
      opening_hours: "08:00",
      description: "natus",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=15.019916606641281",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 37,
      name: "Jairo Bahringer",
      tel: "255.038.2144 x3477",
      address: "0007 Stroman Burg",
      opening_hours: "08:00",
      description: "Non dolore quibusdam.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=53.219186519462404",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 38,
      name: "Miss Lowell Cartwright",
      tel: "1-547-151-9912",
      address: "8071 Mia Corner",
      opening_hours: "08:00",
      description:
        "Id laboriosam et repellendus voluptatum amet sit. Autem nostrum provident libero pariatur dignissimos eum at occaecati. Accusamus minus labore earum laudantium nulla distinctio.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=81.33209937017763",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 39,
      name: "Sigurd Schulist",
      tel: "302.430.7394 x97414",
      address: "7341 Runolfsson Islands",
      opening_hours: "08:00",
      description:
        "Voluptatum ut nam vitae voluptas.\nVoluptas et praesentium voluptas ipsa.\nEt ad velit facilis et est eius eum debitis ratione.\nSed eum assumenda exercitationem omnis totam excepturi voluptates.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=54.810563400984826",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 40,
      name: "Belle Schultz",
      tel: "386-773-4806 x0598",
      address: "266 Satterfield Plains",
      opening_hours: "08:00",
      description:
        "Ullam omnis qui consequatur natus adipisci. Velit quo omnis ea ipsam harum et voluptas. Ullam dolor autem adipisci. Perferendis et libero mollitia voluptatem aspernatur dolor sit maxime.\n \rUnde qui et fuga eos et eaque animi repellat. Qui cupiditate id fuga esse id exercitationem. Soluta nesciunt beatae vitae ducimus odio quia dicta.\n \rDebitis exercitationem non mollitia quo deserunt consequuntur consectetur. Nostrum et voluptas molestiae quia officiis. Tenetur rerum laborum ipsum sed iste aspernatur consequatur. Enim odio asperiores deleniti in placeat minima non.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=50.21868052725837",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 41,
      name: "Rodger Cassin",
      tel: "725.174.1801 x48546",
      address: "321 Marlin Highway",
      opening_hours: "08:00",
      description:
        "Voluptas exercitationem quo eius non.\nMagnam harum sunt ratione consectetur quibusdam beatae minus.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=67.45064701988537",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 42,
      name: "Ellis Borer",
      tel: "(483) 157-8015",
      address: "543 Adolfo Route",
      opening_hours: "08:00",
      description:
        "Rerum magnam non dolorem. Odit quia eveniet nulla minima distinctio temporibus. Dolores quo esse modi totam.\n \rOfficiis deleniti non quo modi facere consequatur eligendi non. Laudantium asperiores enim officia vitae quia voluptas ut voluptatem neque. Esse at voluptas. Repellat repellendus officiis voluptas laborum ab modi. Perspiciatis odio et.\n \rAut aut iste adipisci quo fugiat asperiores. Id architecto eos et fugiat molestias. Non rem itaque consequatur repellendus corporis minima nihil.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=43.963422673486896",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 43,
      name: "Leilani Farrell",
      tel: "1-762-367-5029 x505",
      address: "9624 Gleason Forest",
      opening_hours: "08:00",
      description:
        "Autem cupiditate blanditiis facere ullam hic consequatur et. Voluptatem et ut. Hic ad hic deleniti dolor veritatis. Quas quia ut et et dolor quis sed magnam. Laudantium omnis et commodi alias doloribus repellendus enim eius ab.\n \rVoluptatum hic provident rerum sed eos voluptatum mollitia ut. Voluptatem sint expedita sit vero velit in dolorem tempore labore. Et laborum et recusandae harum.\n \rExcepturi nam voluptatem qui totam ut totam nam. Et dolores ratione. Voluptas quos dolor aut quaerat. Qui sed ratione. Aut id ut dicta ea voluptatem blanditiis quae.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=98.88613237043953",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 44,
      name: "Ed Stracke",
      tel: "1-658-666-5909",
      address: "50571 Runte Greens",
      opening_hours: "08:00",
      description: "incidunt dignissimos porro",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=91.0493955495603",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 45,
      name: "Alia O'Conner Sr.",
      tel: "872-301-8435 x7758",
      address: "68771 Hammes Row",
      opening_hours: "08:00",
      description:
        "Quasi eius sequi sunt sapiente vel.\nImpedit quaerat voluptate ut nemo voluptatum sit praesentium temporibus.\nDoloribus cumque sapiente amet id vero in totam.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=1.0481977419990685",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 46,
      name: "Everardo Reichel",
      tel: "712-859-2804",
      address: "0114 Corrine Views",
      opening_hours: "08:00",
      description:
        "At et enim.\nEa dignissimos quibusdam voluptatem nesciunt earum ut.\nAutem eum laborum ullam sequi possimus.\nLaborum et incidunt nam harum sit dolorem illo voluptate quas.\nAsperiores blanditiis quia aut tempora quas soluta rerum delectus ut.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=71.15578389427839",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 47,
      name: "Harold Jacobson",
      tel: "(858) 695-6808",
      address: "63463 Buck Stream",
      opening_hours: "08:00",
      description: "et",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=67.26227176332283",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 48,
      name: "Eda Crist",
      tel: "375-354-8129 x17211",
      address: "80611 Bernhard Mews",
      opening_hours: "08:00",
      description: "animi rerum repudiandae",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=64.404766436467",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 49,
      name: "Kayleigh Cremin",
      tel: "(122) 464-9775 x6528",
      address: "62263 Schamberger Mountains",
      opening_hours: "08:00",
      description: "Molestiae qui dolorum omnis.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=47.23822856124287",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
    {
      id: 50,
      name: "Alexie Pacocha",
      tel: "(249) 322-0854",
      address: "199 Erdman Trafficway",
      opening_hours: "08:00",
      description:
        "Dolorem ut corrupti. Dolores ut occaecati sunt quae placeat aliquam ea et minima. Consequatur accusamus sequi pariatur ut itaque ut quidem esse voluptatem. Iste occaecati tenetur. Quae et perferendis et pariatur odio ipsa rem.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=12.248914951124569",
      viewCounts: 0,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-01-31T07:49:12.000Z",
        updatedAt: "2022-01-31T07:49:12.000Z",
      },
    },
  ],
};

export default {
  data() {
    return {
      restaurants: [],
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants;
    },
    deleteRestaurant(restaurantId) {
      this.restaurants = this.restaurants.filter(restaurant => restaurant.id !== restaurantId)
    }
  },
};
</script>