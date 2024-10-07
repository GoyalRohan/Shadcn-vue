<template>
  <div class="py-8 flex justify-center">
    <Popover>
      <PopoverTrigger as-child>
        <Button class="bg-blue-500">
          <Filter class="mr-3"/>
          <span class="font-bold">Filter: </span><span class="ml-1">All</span>
        </Button>
      </PopoverTrigger>
      <PopoverContent class="w-80">
        <div class="grid gap-4">
          <div class="space-y-2">
            <h4 class="font-medium leading-none">Filter by</h4>

            <div class="border border-gray-200"></div>
          </div>

          <div>
            <RadioGroup default-value="All">
              <div class="flex items-center space-x-2 mb-1">
                <RadioGroupItem id="r1" value="ALL" />
                <Label for="r1">All</Label>
              </div>
              
              <div class="flex items-center space-x-2 mb-1">
                <RadioGroupItem id="r2" value="User" />
                <Label for="r2">User</Label>
              </div>

              <div class="mb-1">
                <Accordion type="single" class="w-full" collapsible>
                  <AccordionItem
                    v-for="item in accordionItems1"
                    :key="item.value"
                    :value="item.value"
                    class="!border-b-0"
                  >
                    <AccordionTrigger class="py-0 hover:no-underline">
                      <div class="flex items-center space-x-2">
                        <RadioGroupItem id="r3" value="Category" />
                        <Label for="r3">Category</Label>
                      </div>
                    </AccordionTrigger>
                    <AccordionContent>
                      <DropdownMenu>
                        <DropdownMenuTrigger as-child>
                          <Button variant="outline" class="mt-3 h-7"> Select a Category </Button>
                        </DropdownMenuTrigger>
                        <DropdownMenuContent class="w-56">
                          <DropdownMenuItem>Add Product Asset</DropdownMenuItem>
                          <DropdownMenuItem
                            >Clone Library Assets</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Import Library Assets</DropdownMenuItem
                          >
                          <DropdownMenuItem>Import Product</DropdownMenuItem>
                          <DropdownMenuItem
                            >Import Product Assets</DropdownMenuItem
                          >
                          <DropdownMenuItem>Manage Users</DropdownMenuItem>
                          <DropdownMenuItem>Product Bundles</DropdownMenuItem>
                          <DropdownMenuItem>Product Family</DropdownMenuItem>
                          <DropdownMenuItem>Product Overview</DropdownMenuItem>
                          <DropdownMenuItem
                            >Product Workflow Management</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Release Management</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Remove Product Asset</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Removed Library Assets</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Replace Asset Dependencies</DropdownMenuItem
                          >
                          <DropdownMenuItem
                            >Update Product Data</DropdownMenuItem
                          >
                        </DropdownMenuContent>
                      </DropdownMenu>
                    </AccordionContent>
                  </AccordionItem>
                </Accordion>
              </div>

              <div class="mb-1">
                <Accordion type="single" class="w-full" collapsible>
                  <AccordionItem
                    v-for="item in accordionItems1"
                    :key="item.value"
                    :value="item.value"
                    class="!border-b-0"
                  >
                    <AccordionTrigger  class="py-0 hover:no-underline">
                      <div class="flex items-center space-x-2">
                        <RadioGroupItem id="r4" value="Time" />
                        <Label for="r4">Time</Label>
                      </div>
                    </AccordionTrigger>
                    <AccordionContent>
                      <Popover>
                        <PopoverTrigger as-child>
                          <Button
                            variant="outline"
                            :class="
                              cn(
                                'w-[280px] justify-start text-left font-normal mt-3 h-7',
                                !value && 'text-muted-foreground'
                              )
                            "
                          >
                            <CalendarIcon class="mr-2 h-4 w-4" />
                            <template v-if="value.start">
                              <template v-if="value.end">
                                {{
                                  df.format(
                                    value.start.toDate(getLocalTimeZone())
                                  )
                                }}
                                -
                                {{
                                  df.format(
                                    value.end.toDate(getLocalTimeZone())
                                  )
                                }}
                              </template>

                              <template v-else>
                                {{
                                  df.format(
                                    value.start.toDate(getLocalTimeZone())
                                  )
                                }}
                              </template>
                            </template>
                            <template v-else> Pick a date </template>
                          </Button>
                        </PopoverTrigger>
                        <PopoverContent class="w-auto p-0">
                          <RangeCalendar
                            v-model="value"
                            initial-focus
                            :number-of-months="2"
                            @update:start-value="
                              (startDate) => (value.start = startDate)
                            "
                          />
                        </PopoverContent>
                      </Popover>
                    </AccordionContent>
                  </AccordionItem>
                </Accordion>
              </div>
            </RadioGroup>
          </div>
        </div>
      </PopoverContent>
    </Popover>
  </div>
</template>

<script setup lang="ts">
import {
  Popover,
  PopoverContent,
  PopoverTrigger,
} from "@/components/ui/popover";
import { Button } from "@/components/ui/button";
import { Label } from "@/components/ui/label";
import { Input } from "@/components/ui/input";
import { RadioGroup, RadioGroupItem } from "@/components/ui/radio-group";
import {
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from "@/components/ui/accordion";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuItem,
  DropdownMenuLabel,
  DropdownMenuSeparator,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";
import {
  CalendarDate,
  DateFormatter,
  getLocalTimeZone,
} from "@internationalized/date";
import { cn } from '@/lib/utils'

import { Calendar as CalendarIcon } from "lucide-vue-next";
import { Filter } from 'lucide-vue-next';
import type { DateRange } from "radix-vue";
import { RangeCalendar } from "@/components/ui/range-calendar";

const df = new DateFormatter("en-US", {
  dateStyle: "medium",
});

const value = ref({
  start: new CalendarDate(2022, 1, 20),
  end: new CalendarDate(2022, 1, 20).add({ days: 20 }),
}) as Ref<DateRange>;

const accordionItems1 = [
  {
    value: "item-1",
    title: "Is it accessible?",
    content: "Yes. It adheres to the WAI-ARIA design pattern.",
  },
];

const accordionItems2 = [
  {
    value: "item-1",
    title: "Is it accessible?",
    content: "Yes. It adheres to the WAI-ARIA design pattern.",
  },
];
</script>
